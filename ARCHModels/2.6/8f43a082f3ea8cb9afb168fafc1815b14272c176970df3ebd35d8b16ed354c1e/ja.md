```
fit!(am::ARCHModel; algorithm=BFGS(), autodiff=:forward, kwargs...)
```

指定された `am` によって単変量または多変量 ARCHModel をフィットし、`am` をその場で変更します。キーワード引数は最適化プログラムに渡されます。
