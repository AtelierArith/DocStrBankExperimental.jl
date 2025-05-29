```
NeighborhoodRule <: Rule
```

現在のセルを中心とした近傍にのみアクセスするルールです。`NeighborhoodRule`は次のメソッドで適用されます：

```julia
applyrule(data::AbstractSimData, rule::MyNeighborhoodRule, state, I::Tuple{Int,Int})
```

`NeighborhoodRule`は、[`Neighborhood`](@ref)オブジェクトを保持する`neighborhood`メソッドまたはフィールドを持っている必要があります。`neighbors(rule)`は、`Neighborhood`によって定義された周囲のセルパターンに対するイテレータを返します。

グリッド内の各セルに対して、近傍バッファが`applyrule`メソッドで使用するために更新され、配列の読み取りを最小限に抑えるように管理されます。

これにより、メモリの最適化と近傍バッファに対する高性能ルーチンの使用が可能になります。また、近傍コードでは境界チェックが不要であることも意味します。

複数の読み取りグリッドを持つ近傍ルールの場合、最初のグリッドが常に近傍に使用され、他のグリッドはセルの追加状態として渡されます。任意のグリッドに書き込むことができますが、現在のセルに対してのみです。
