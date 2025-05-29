```
contract(x, y, ::Val{N})
```

$$
N
$$

の内部インデックスの収縮を行います。例えば、$N=2$ の収縮は三次元テンソル $A_{ij} = B_{ikl} C_{klj}$ の場合、次のように計算できます：

# 例

```jldoctest
julia> B = rand(Tensor{Tuple{3,3,3}});

julia> C = rand(Tensor{Tuple{3,3,3}});

julia> A = contract(B, C, Val(2))
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 3.70978  2.47156  3.91807
 2.90966  2.30881  3.25965
 1.78391  1.38714  2.2079
```

特定の収縮のために次の中置演算子も利用可能です：

  * `x ⊡ y` （`⊡` は `\boxdot<tab>` で入力可能）: `contract(x, y, Val(1))`
  * `x ⊡₂ y` （`⊡₂` は `\boxdot<tab>\_2<tab>` で入力可能）: `contract(x, y, Val(2))`
  * `x ⊗ y` （`⊗` は `\otimes<tab>` で入力可能）: `contract(x, y, Val(0))`
