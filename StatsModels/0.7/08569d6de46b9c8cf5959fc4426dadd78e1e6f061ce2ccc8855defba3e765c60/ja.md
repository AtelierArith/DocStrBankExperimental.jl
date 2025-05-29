```
unprotect(term)
unprotect(::Protected{T})
```

[`@formula`]内で、引数termの[`Protected`](@ref)ステータスを削除します。これにより、通常の[`Protected`](@ref)コンテキスト内で`+`、`&`、`*`、および`~`への呼び出しの[`@formula`](@ref)特有の解釈が復元されます。

`@formula`の外で呼び出されると、`Protected{T}`を`T`にアンラップします。

# 例

```jldoctest; setup = :(using Random; Random.seed!(1))
julia> d = (y=rand(4), a=[1.:4;], b=rand(4));

julia> f = @formula(y ~ 1 - unprotect(a&b));

julia> modelmatrix(f, d)
4×1 Matrix{Float64}:
  0.08507099633716864
  0.6143837675082491
 -1.310541043656999
 -2.1220770547007453

julia> 1 .- d.a .* d.b
4-element Vector{Float64}:
  0.08507099633716864
  0.6143837675082491
 -1.310541043656999
 -2.1220770547007453
```
