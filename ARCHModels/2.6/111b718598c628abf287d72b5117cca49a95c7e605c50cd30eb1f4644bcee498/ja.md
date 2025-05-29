```
fit(am::ARCHModel; algorithm=BFGS(), autodiff=:forward, kwargs...)
```

指定された `am` の単変量または多変量 ARCHModel をフィットし、結果を新しい `ARCHModel` のインスタンスで返します。キーワード引数はオプティマイザに渡されます。
