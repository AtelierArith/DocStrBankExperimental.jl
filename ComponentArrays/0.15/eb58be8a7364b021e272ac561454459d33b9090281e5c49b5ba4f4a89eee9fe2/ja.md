```
valkeys(x::ComponentVector)
valkeys(x::AbstractAxis)
```

`ComponentVector`の`Val`でラップされたキーを返し、コンポーネントキーの高速な反復処理を可能にします。`AbstractAxis`にも直接機能します。

# 例

```jldoctest
julia> using ComponentArrays

julia> ca = ComponentArray(a=1, b=[1,2,3], c=(a=4,))
ComponentVector{Int64}(a = 1, b = [1, 2, 3], c = (a = 4))

julia> [ca[k] for k in valkeys(ca)]
3-element Vector{Any}:
 1
  [1, 2, 3]
  ComponentVector{Int64}(a = 4)

julia> sum(prod(ca[k]) for k in valkeys(ca))
11
```
