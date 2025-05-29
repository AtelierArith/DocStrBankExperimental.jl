```
struct FunctionWrapper <: AbstractFunction
    f::Function
    dim::Int
end
```

関数 `f` をラップする関数ラッパー型であり、関数 `f` は次元 `dim` の出力を返すことが宣言されています。
