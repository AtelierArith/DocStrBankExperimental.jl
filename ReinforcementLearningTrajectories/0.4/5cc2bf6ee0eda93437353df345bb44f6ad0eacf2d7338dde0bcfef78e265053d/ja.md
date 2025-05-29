```
Trace(A::AbstractArray)
```

`Julia@v1.9`で導入される[`Slices`](https://github.com/JuliaLang/julia/blob/master/base/slicearray.jl)に似ています。主な違いは、`Slices`の`axes`情報が静的であるのに対し、`Trace`では動的である可能性があることです。

RLでの最も一般的な使用法であるため、最後の次元に沿ったスライスのみをサポートしています。
