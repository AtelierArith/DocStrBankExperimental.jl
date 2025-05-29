```julia
struct Outport{P} <: Causal.AbstractPort{P}
```

`Outport`を`numpins` [`Outpin`](@ref)で構築します。

# フィールド

  * `pins::Vector`: 出力ポートのピン
  * `id::Base.UUID`: 一意の識別子

!!! warning `Outport`の要素型は`Outpin`でなければなりません。詳細は[`Outpin`](@ref)を参照してください。

# 例

```jldoctest
julia> Outport{Int}(2)
2-element Outport{Outpin{Int64}}:
 Outpin(eltype:Int64, isbound:false)
 Outpin(eltype:Int64, isbound:false)

julia> Outport()
1-element Outport{Outpin{Float64}}:
 Outpin(eltype:Float64, isbound:false)
```
