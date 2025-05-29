```
SolitaryWaveWhithamGreenNaghdi(param; kwargs)
```

指定された速度を持つWhitham-Green-Naghdi孤立波を計算します。

# 引数

  * `param :: NamedTuple`: 速度 `c` と無次元パラメータ `ϵ` と `μ`、メッシュサイズ `L` とコレクションポイントの数 `N` を含む問題のパラメータ;

## キーワード（オプション）

  * `guess :: Vector{Real}`: 表面変形の初期推測（提供されていない場合、SGNの正確な式が使用されます）;
  * `x₀ :: Real`: 孤立波の中心（推測が提供されていない場合）;
  * `SGN :: Bool`: `true` の場合、Serre-Green-Naghdi（Whitham-Green-Naghdiの代わりに）孤立波を計算します（代わりに `SolitaryWaveSerreGreenNaghdi` を考慮してください）;
  * `method :: Int`: 使用される方程式（`1` と `4` の間）;
  * `iterative :: Bool`: `true` の場合はGMRESを通じてヤコビアンを反転し、`false` の場合はLU分解（デフォルトは `false`）;
  * `verbose :: Bool`: `true` の場合は各ステップで数値誤差を印刷します（デフォルトは `false`）;
  * `max_iter :: Int`: ニュートンアルゴリズムの最大反復回数（デフォルトは `20`）;
  * `tol :: Real`: ℓ∞ノルムで測定された相対許容誤差（デフォルトは `1e-10`）;
  * `ktol :: Real`: Krasnyフィルターの許容誤差（デフォルトは `0`、すなわちフィルタリングなし）;
  * `gtol :: Real`: GMRESアルゴリズムの相対許容誤差（デフォルトは `1e-10`）;
  * `dealias :: Int`: Orliczルールによるディーリアリング `1-dealias/(dealias+2)`（デフォルトは `0`、すなわちディーリアリングなし）;
  * `q :: Real`: `u_{n+1}=q*u_{n+1}+(1-q)*u_n` で修正されたニュートンアルゴリズム（デフォルトは `1`）;
  * `α :: Real`: ヤコビアンにカーネルへのスペクトル射影を `α` 倍追加します（デフォルトは `0`）。

# 戻り値

`(η,u,v,mesh)` で、

  * `η :: Vector{Float64}`: 表面変形;
  * `u :: Vector{Float64}`: 層平均速度;
  * `v :: Vector{Float64}`: 表面での速度ポテンシャルの導関数;
  * `mesh :: Mesh`: メッシュコレクションポイント。
