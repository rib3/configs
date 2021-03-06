Notes for [goacccess](https://goaccess.io), a web log analyzer

# examples

## s3 logs

> versions after 1.0.2 should enable `--log-format=AWSS3`

> https://github.com/allinurl/goaccess/commit/906812f

### single log file, use s3 config
```
cat LOG_FILE | goaccess -p ~/dotfiles/goaccess/s3
```

### some files

```
cat * | goaccess -p ~/dotfiles/goaccess/s3
```

> `cat *` may run into `Argument list too long`

> The error from `cat` will be hidden by the `goaccess` screen takeover

### lots of files

```
# `-exec ... +` will combine args (similar to xargs)
# greatly speeds things up by reducing the amount of spawned processes
find . -type f -exec cat {} + | goaccess -p ~/dotfiles/goaccess/s3
```

### lots of files by filename
```
find -name "2016-11-03*" -exec cat {} + | goaccess -p ~/dotfiles/goaccess/s3
```
