```
Mesh(p::Params; args...)
```

生成されたメッシュには、自由度の番号付けと、与えられた [`Scenario`](@ref) のすべての基底関数が含まれています。

この構造体には、シナリオに依存しない以下のフィールドが含まれています：

  * `num1el` –> $ζ^1$ 方向の要素数
  * `num2el` –> $ζ^2$ 方向の要素数
  * `numel` –> 面積要素の数
  * `num1np` –> $ζ^1$ 方向のノードポイント数
  * `num2np` –> $ζ^2$ 方向のノードポイント数
  * `numnp` –> 2次元メッシュ上のノードポイント数
  * `IX` –> 各面積要素の非ゼロノード番号を含む行列
  * `bdry_elems` –> [`Boundary`](@ref) から要素番号へのマッピング
  * `crnr_elems` –> [`Corner`](@ref) から要素番号へのマッピング
  * `bdry_nodes` –> [`Boundary`](@ref) からノード番号へのマッピング
  * `bdry_inner_nodes` –> [`Boundary`](@ref) から内部ノード番号へのマッピング
  * `crnr_nodes` –> [`Corner`](@ref) からノード番号へのマッピング
  * `crnr_inner_nodes` –> [`Corner`](@ref) から内部ノード番号へのマッピング
  * `kv1` –> $ζ^1$ 方向の [`KnotVector`](@ref)
  * `kv2` –> $ζ^2$ 方向の [`KnotVector`](@ref)
  * `area_gp_fns` –> [`AreaGpBasisFns`](@ref): 2次元面積基底関数
  * `bdry_gp_fns` –> [`Boundary`](@ref) から [`BdryGpBasisFns`](@ref) へのマッピング
  * `crnr_gp_fns` –> [`Corner`](@ref) から2次元基底関数 [`GpBasisFnsζα`](@ref) へのマッピング

生成されたメッシュは、解決される問題に依存します。関数 [`generate_scenario`](@ref MembraneAleFem.generate_scenario) は、`Bc.jl` からのシナリオ特有の結果を使用して、以下のシナリオ依存フィールドを設定します：

  * `topology` –> 表面の [`Topology`](@ref)
  * `dofs` –> グローバル順序のアクティブな [`Unknown`](@ref Dof.Unknown) のリスト
  * `ndf` –> アクティブな [`Unknown`](@ref Dof.Unknown) の数
  * `ID` –> ノード番号をそのノードの未知数のインデックスにマッピングする行列
  * `ID_inv` –> `ID` の逆：`unknown_id` を `(node_number, dof_number)` にマッピング
  * `nmdf` –> メッシュの自由度の総数
  * `LM` –> 面積要素からその要素のすべての未知数のインデックスへのマッピング
  * `inh_dir_bcs` –> 非均質ディリクレ境界条件のリスト
  * `inh_neu_bcs` –> 非均質ノイマン境界条件のリスト

```
