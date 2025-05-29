```
auxquadgk!(f::BatchIntegrand, result, a,b,c...; kws...)
```

[`auxquadgk!`](@ref)と同様ですが、インプレースの積分関数に対して評価ポイントをバッチ処理して同時に評価します。特に、`BatchIntegrand`を使用して`quadgk`を使用する場合との違いは2つあります。

1. `f.y`は、最初の`axes`が`result`のものと一致する次元`ndims(result)+1`の配列でなければなりません。`y`の最後の次元は異なるKronrodポイントのために予約されている必要があり、関数`f.f!`は次の形式である必要があります。`f!(y,x) = foreach((v,z) -> v .= f(z), eachslice(y, dims=ndims(y)), x)`または

    function f!(y, x)      idx = CartesianIndices(axes(y)[begin:end-1])      for (j,i) in zip(axes(y)[end], eachindex(x))          y[idx,j] .= f(x[i])      end  end
2. `f.y`は最後の次元で`resize!`可能でなければなりません。これには[ElasticArrays.jl](https://github.com/JuliaArrays/ElasticArrays.jl)の使用を検討してください。そうでない場合は、配列型`T`に対して`QuadGK.resizelastdim!(A::T, n)`を特化してください。
