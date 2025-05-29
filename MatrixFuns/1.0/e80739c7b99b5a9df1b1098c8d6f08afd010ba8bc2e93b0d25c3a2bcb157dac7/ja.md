```
mat_fun_frechet(f, H::AbstractMatrix, h::Vector{AbstractMatrix}; kwargs...)
mat_fun_frechet(DD_F, Ψ::AbstractMatrix, h::Vector{AbstractMatrix})
```

n 階フレシェ微分 `d^nf(H)h[1]…h[n]` を返します。ここで、`f` は `f(x)` として呼び出されると仮定します。可能なキーワード引数の説明については `mat_fun` を参照してください。
