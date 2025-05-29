```
mutable struct DestripingData{T <: Real, O <: Healpix.Order}
```

デストライピング操作の結果を含む構造体です。以下のフィールドを含みます：

  * `skymap`: 最大尤度マップを含む `PolarizedMap`
  * `hitmap`: 各ピクセルの重みを含むマップ（これはヒットカウントではなく、TODの各サンプルに対する $σ^2$ の値で正規化されています）
  * `nobs_matrix`: I/Q/U コンポーネントの再構成で最も問題のあったピクセルを特定するために使用できる [`NobsMatrixelement`](@ref) オブジェクトの配列
  * `baselines`: 計算されたベースライン。これらは `RunLengthArray` オブジェクトのリストとして保持する必要があります
  * `stopping_factors`: CGアルゴリズムの各反復に対するストッピングファクターのシーケンス
  * `threshold`: 共役勾配法に対する許容誤差の上限（オプション、デフォルトは `1e-9`）。[`calc_stopping_factor`](@ref) を参照してください。
  * `max_iterations`: 共役勾配アルゴリズムに対する許可された最大反復回数（オプション、デフォルトは `1000`）。
  * `use_preconditioner`: プレコンディショナーを使用するかどうかを示すブールフラグ（オプション、デフォルトは `true`）。通常、これを `true` にしたいです。

この構造体は、以下のパラメータを受け取る唯一のコンストラクタを提供します：

  * `nside`: `skymap` と `hitmap` の解像度
  * `obs_list`: [`Observation`](@ref) のベクター；マップ内で観測されるピクセルを特定するために使用されます
  * `runs`: 各観測に対する各ベースラインに含まれるサンプル数を含むベクターのリスト（`obs_list` の各要素に対して1つ）

コンストラクタは以下のキーワードも受け取ります：

  * `threshold`（デフォルト: `1e-9`）
  * `max_iterations`（デフォルト: 1000）
  * `use_preconditioner`（デフォルト: `true`）

関数 [`destripe!`](@ref) は `DestripingData` を使用して計算の結果を返します。
