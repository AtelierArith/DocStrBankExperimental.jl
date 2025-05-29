```
random_orthog(n::Int,m::Int)::Matrix{Float64}
random_orthog(::Type{ElT},n::Int,m::Int)::Matrix{ElT}
```

次の条件を満たすランダムな実行列 O を返します。O の次元は (n,m) であり、n >= m の場合は transpose(O)*O が単位行列になり、m > n の場合は O*transpose(O) が単位行列になります。オプションで、最初の引数に実数型を渡すことで、その型の行列を取得できます。
