```
struct Physics
```

次のフィールドを持つ物理データレコード：

  * `flux::Function`: 隣接する制御体積間のフラックス：`flux(f,u,edge,data)`は、隣接する制御体積の外心を結ぶエッジに沿った種iのフラックスを`f[i]`に返す必要があります。uは2D配列で、種iについては、`u[i,1]`と`u[i,2]`がエッジの対応する端の未知の値を含みます。
  * `storage::Function`: ストレージ項（時間微分の下の項）：`storage(f,u,node,data)`

    これは、i番目の方程式のストレージ項を`f[i]`に返す必要があります。`u[i]`はi番目の未知の値を含みます。
  * `reaction::Function`: 反応項：`reaction(f,u,node,data)`

    これは、i番目の方程式の反応項を`f[i]`に返す必要があります。`u[i]`はi番目の未知の値を含みます。
  * `edgereaction::Function`: エッジ反応項：`edgereaction(f,u,edge,data)`

    これは、i番目の方程式の反応項を`f[i]`に返す必要があります。`u[i]`はi番目の未知の値を含みます。uは2D配列で、種iについては、`u[i,1]`と`u[i,2]`がエッジの対応する端の未知の値を含みます。
  * `source::Function`: ソース項：`source(f,node,data)`。

    これは、i番目の方程式のソース項の値を`f[i]`に返す必要があります。
  * `bflux::Function`: 境界上の隣接する制御体積間のフラックス。境界に完全に隣接するエッジで呼び出されます：`bflux(f,u,bedge,data)`
  * `breaction::Function`: 境界反応項：`breaction(f,u,node,data)` 反応に似ていますが、内側または外側の境界に制限されています。
  * `bsource::Function`: 境界ソース項：`bsource(f,node,data)`。

    これは、i番目の方程式のソース項の値を`f[i]`に返す必要があります。
  * `bstorage::Function`: 境界ストレージ項：`bstorage(f,u,node,data)` ストレージに似ていますが、内側または外側の境界に制限されています。
  * `boutflow::Function`: 流出境界項 `boutflow(f,u,edge,data)` この関数は、少なくとも1つのODEが流出境界の1つにあるエッジ（内部のものを含む）に対して呼び出されます。この関数内では、[`outflownode`](@ref)および[`isoutflownode`](@ref)を使用してそのノードを特定できます。両方のノードが流出ノードである場合にはいくつかの曖昧さがありますが、その場合は寄与がゼロであると仮定されます。
  * `outflowboundaries::Vector{Int64}`: 流出境界条件を持つ境界領域のリスト（ベクター）。`boutflow`が呼び出されるときに影響します。
  * `generic_operator::Function`: 一般的な演算子 `generic_operator(f,u,sys)`。この演算子は、システムの完全な解`u`に作用します。スパース性は、`generic_operator_sparsity`が指定されていない限り、自動的に検出されます。
  * `generic_operator_sparsity::Function`: 一般的な演算子のスパース構造を定義する関数。これは、`generic_operator`のスパースパターンを返す必要があります。
  * `data::Any`: ユーザーデータ（パラメータ）。これにより、さまざまなパラメータをコールバック関数に渡すことができます。
  * `num_species::Int8`: 境界種を含む種の数。意味がなく、非推奨です。
