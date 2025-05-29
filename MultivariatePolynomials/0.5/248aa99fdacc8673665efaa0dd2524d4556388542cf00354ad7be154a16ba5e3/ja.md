```
struct Graded{O<:AbstractMonomialOrdering} <: AbstractMonomialOrdering
    same_degree_ordering::O
end
```

モノミアル順序は次のように定義されます：

  * `degree(a) == degree(b)` の場合、順序は `same_degree_ordering` によって決まります。
  * それ以外の場合、順序は整数 `degree(a)` と `degree(b)` の間の順序です。
