```
 generic_group(G, op)
```

集合 $G$ 上の演算 $op$ による群を計算します。

三つ組 `(Gen, GtoGen, GentoG)` を返します。ここで `Gen` は群、`GtoGen` は `G` の要素を `Gen` の要素にマッピングする辞書、`GentoG` はその逆です。

# 例

```jldoctest
julia> G = [1, -1, im, -im]
4-element Vector{Complex{Int64}}:
  1 + 0im
 -1 + 0im
  0 + 1im
  0 - 1im

julia> Gen, GtoGen, GentoG = generic_group(G, *);

julia> Gen
Generic group of order 4 with multiplication table

julia> one(Gen)
(1)

julia> GentoG[one(Gen)]
1 + 0im

julia> GtoGen[-1]
(2)
```
