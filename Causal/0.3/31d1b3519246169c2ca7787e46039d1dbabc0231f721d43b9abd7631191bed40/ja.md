```julia
struct Inport{P} <: Causal.AbstractPort{P}
```

`Inport`を`numpins` [`Inpin`](@ref)で構築します。

# フィールド

  * `pins::Vector`: ポートのピン

!!! warning `Inport`の要素型は`Inpin`でなければなりません。詳細は[`Inpin`](@ref)を参照してください。

# 例

```jldoctest
julia> Inport{Int}(2)
2-element Inport{Inpin{Int64}}:
 Inpin(eltype:Int64, isbound:false)
 Inpin(eltype:Int64, isbound:false)

julia> Inport()
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
