```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

`iftrue`が`true`の場合、`sysfunc`の記述的な文字列を持つ`errno`に対して`SystemError`を発生させます。
