```
zticks(p::Plot)
```

は、`p`のサブプロットのz軸の目盛りのベクトルを返します。

使用例：

```jldoctest
julia> p = plot(1:5, zticks=[1,2])

julia> zticks(p)
1-element Vector{Tuple{Vector{Float64}, Vector{String}}}:
 ([1.0, 2.0], ["1", "2"])
```

もし`p`が単一のサブプロットで構成されている場合、最初の要素だけを取得したい場合は、

```jldoctest
julia> zticks(p)[1]
([1.0, 2.0], ["1", "2"])
```

または、`p`の最初（唯一）のサブプロットに対してzticksを呼び出すこともできます。

```jldoctest
julia> zticks(p[1])
([1.0, 2.0], ["1", "2"])
```
