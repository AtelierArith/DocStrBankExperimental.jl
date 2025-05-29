```
findmaximal(sitegs::AbstractVector{<:SiteGroup})
```

`AbstractVector{<:SiteGroup}`を持つ空間群の異なるワイコフ位置に対して、最大のワイコフ位置に関連する`SiteGroup`を返します。

結果は入力ベクトルへの`view`として返されます（すなわち、`AbstractVector{<:SiteGroup}`として）。関連するワイコフ位置は[`position`](@ref)を介して取得できます。

## 定義

ワイコフ位置は、そのサイト対称群が「近くの」ワイコフ位置のサイト対称群よりも高次である場合に最大と見なされます（すなわち、考慮されるワイコフ位置にパラメータの変動を通じて接続できるワイコフ位置）。

## 例

```jldoctest
julia> sgnum = 5;

julia> D = 2;

julia> sg  = spacegroup(sgnum, Val(D));

julia> sitegs = sitegroups(sg)
2-element Vector{SiteGroup{2}}:
 [1] (4b: [α, β])
 [1, m₁₀] (2a: [0, β])

julia> only(findmaximal(sitegs))
SiteGroup{2} ⋕5 (c1m1) at 2a = [0, β] with 2 operations:
 1
 m₁₀
```
