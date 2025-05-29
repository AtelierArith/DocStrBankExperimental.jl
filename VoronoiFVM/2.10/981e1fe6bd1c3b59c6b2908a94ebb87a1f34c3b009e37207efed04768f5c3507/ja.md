```
System(grid; kwargs...)
```

有限体積システムの解のデータを保持する型 [`VoronoiFVM.System{Tv,Ti, Tm, TSpecMat<:AbstractMatrix, TSolArray<:AbstractMatrix}`](@ref) の構造を作成します。

パラメータ:

  * `grid::ExtendableGrid`: 1D、2D、または3Dの計算グリッド

キーワード引数:

  * `species`: 整数の種インデックスのベクトル。すべてのグリッド領域に追加され、このデフォルトケースでは [`enable_species!`](@ref) を呼び出す必要がありません。空のままにすると、種は作成後に [`enable_species!`](@ref) を介してシステムに追加する必要があります。
  * `unknown_storage`: 文字列またはシンボル。種の分布に関する情報は、スパースまたは密な行列に保持され、それに応じて解の配列は SparseSolutionArray または行列の型になります。スパース未知ストレージの場合、システム行列は未知数に対応する自由度のみを処理します。ただし、未知数の管理のためのスパース行列構造の処理にはオーバーヘッドが発生します。

      * `:dense` : 解ベクトルは `nspecies` x `nnodes` の密な行列です
      * `:sparse` : 解ベクトルは `nspecies` x `nnodes` のスパース行列です
  * `matrixindextype`: 整数型。システム内で作成されるスパース行列のインデックス型。
  * `is_linear`: システムが線形かどうか。線形の場合、解決するために1回のニュートンステップのみが使用されます。
  * `assembly`: `:cellwise`（デフォルト）または `:edgewise` のいずれか。アセンブリループの組織方法を決定します。 `:cellwise` は、外側のループがグリッドセル（三角形、四面体）を通過し、各セルのエッジフラックスとノード反応への寄与が計算されることを意味します。その結果、例えば2Dの場合、すべての内部エッジに対して、フラックス関数が隣接する各セルに対して2回呼び出されます。特に3Dでは、これが大きなオーバーヘッドになります。 `:edgewise` では、これらのエッジの幾何学的因子が事前にアセンブルされ、外側のアセンブリループはすべてのグリッドエッジまたはノードを通過し、隣接するセルが異なる領域に属する場合は別々の呼び出しが行われます。

!!! note
    後のバージョンで `:edgewise` をデフォルトにする予定です。


物理学のキーワード引数:

  * `flux`: 関数。隣接する制御体積間のフラックス: `flux(f,u,edge)` または `flux(f,u,edge,data)` は、隣接する制御体積の外心を結ぶエッジに沿った種 i のフラックスを `f[i]` に返す必要があります。種 i に対して、`u[i,1]` と `u[i,2]` はエッジの対応する端での未知の値を含みます。
  * `storage`: 関数。ストレージ項（時間微分の下の項）: `storage(f,u,node)` または `storage(f,u,node,data)` は、i 番目の方程式のストレージ項を `f[i]` に返す必要があります。 `u[i]` は i 番目の未知の値を含みます。
  * `reaction`: 関数。反応項: `reaction(f,u,node)` または `reaction(f,u,node,data)` は、i 番目の方程式の反応項を `f[i]` に返す必要があります。 `u[i]` は i 番目の未知の値を含みます。
  * `edgereaction`: 関数。エッジ反応項: `edgereaction(f,u,edge)` または `edgereaction(f,u,edge,data)` は、i 番目の方程式の反応項を `f[i]` に返す必要があります。種 i に対して、`u[i,1]` と `u[i,2]` はエッジの対応する端での未知の値を含みます。
  * `source`: 関数。ソース項: `source(f,node)` または `source(f,node,data)`。 i 番目の方程式のソース項の値を `f[i]` に返す必要があります。
  * `bflux`: 関数。境界上の隣接する制御体積間のフラックス
  * `breaction` 関数。境界反応項: `breaction(f,u,node)` または `breaction(f,u,node,data)` 反応に似ていますが、内側または外側の境界に制限されています。
  * `bcondition` 関数。 `breaction` のエイリアス。
  * `bsource`: 関数。境界ソース項: `bsource(f,node)` または `bsource(f,node,data)`。 i 番目の方程式のソース項の値を `f[i]` に返す必要があります。
  * `bstorage`: 関数。境界ストレージ項: `bstorage(f,u,node)` または `bstorage(f,u,node,data)` ストレージに似ていますが、内側または外側の境界に制限されています。
  * `generic_operator`: 関数。一般的な演算子 `generic_operator(f,u,sys)`。この演算子はシステムの完全な解 `u` に作用します。スパース性は、`generic_operator_sparsity` が指定されていない限り、自動的に検出されます。
  * `generic_operator_sparsity`: 一般的な演算子のスパース構造を定義する関数。これは `generic_operator` のスパースパターンを返す必要があります。
  * `nparams`: システムが依存するパラメータの数、および導関数を取得する必要があるパラメータに関して。
  * `data`: ユーザーデータ（パラメータ）。これにより、さまざまなパラメータをコールバック関数に渡すことができます。 `data` が指定されている場合、すべてのコールバック関数は最後の `data` 引数を受け入れる必要があります。そうでない場合、データは明示的に渡されず、構成コールバックは関数が定義されているクロージャからパラメータを取得できます。
  * `matrixtype`: :sparse, :tridiagonal, :banded, :auto。デフォルト: :sparse。 :auto は、空間次元と種の数に応じて密な解ストレージの自動選択を導きます。
