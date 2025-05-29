```
butcher_representation(t::RootedTree)
```

`t::RootedTree`によって導入されたButcherの表現を文字列として返します。したがって、唯一の頂点が根自体である根付き木は`τ`として表されます。他の木の表現は再帰的に定義されます。もし`t₁, t₂, ... tₙ`が根付き木`t`の[`部分木`](@ref)であれば、`t = [t₁ t₂ ... tₙ]`として表されます。複数の部分木が同じである場合、その出現回数は累乗として書かれます。

# 例

```jldoctest
julia> rootedtree([1, 2, 3, 2]) |> butcher_representation
"[[τ]τ]"

julia> rootedtree([1, 2, 3, 3, 2]) |> butcher_representation
"[[τ²]τ]"
```

# 参考文献

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
