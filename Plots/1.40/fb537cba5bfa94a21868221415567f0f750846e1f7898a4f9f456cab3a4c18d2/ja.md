```
yticks(p::Plot)
```

は `p` のサブプロットの y 軸の目盛りのベクトルを返します。

使用例:

```jldoctest
julia> p = plot(1:5, yticks=[1,2])

julia> yticks(p)
1-element Vector{Tuple{Vector{Float64}, Vector{String}}}:
 ([1.0, 2.0], ["1", "2"])
```

もし `p` が単一のサブプロットで構成されている場合、最初の要素だけを取得したい場合は、次のようにします。

```jldoctest
julia> yticks(p)[1]
([1.0, 2.0], ["1", "2"])
```

または、`p` の最初の（唯一の）サブプロットに対して yticks を呼び出すこともできます。

```jldoctest
julia> yticks(p[1])
([1.0, 2.0], ["1", "2"])
```
