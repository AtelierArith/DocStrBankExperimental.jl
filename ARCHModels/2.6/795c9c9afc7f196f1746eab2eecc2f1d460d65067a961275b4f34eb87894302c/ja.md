```
fit(::Type{SD}, data; algorithm=BFGS(), kwargs...)
```

データに標準化された分布を適合させ、MLEを使用します。キーワード引数は最適化プログラムに渡されます。
