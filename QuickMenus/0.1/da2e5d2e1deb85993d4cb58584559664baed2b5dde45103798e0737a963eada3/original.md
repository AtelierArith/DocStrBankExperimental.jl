```
filepicker([path=pwd()]; done="--DONE--")
```

Interactively build a path using [`fzf`](https://github.com/junegunn/fzf). If a file is selected, it will return immediately. Select `..` to move to the parent directory. If a directory is selected, `filepicker` will be called recurssively on that directory; choose `--DONE--` to return the directory, or continue selecting.
