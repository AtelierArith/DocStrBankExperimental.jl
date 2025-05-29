```julia
BinarySearch(target::Float64, xRange::Tuple{Float64, Float64}, f::T, args::Tuple ; tol::Float64=0.001)
```

単調関数 f(x, args...)=target に対して、範囲 x ∈ xRange での二分探索を実装する一般的な関数です。許容誤差は tol です。
