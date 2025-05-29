```
(tc::TypedCallable{A,R})(args...; kwargs...)
```

1. `args isa A` を強制します
2. 提供された位置引数とキーワード引数で `tc.f` を呼び出します
3. 上記の呼び出しの戻り値の型を `R` として強制します
