```
SolitaryWaveWhitham(param; kwargs)
```

指定された速度でWhitham孤立波を計算します。

# 引数

  * `param :: NamedTuple`: 速度 `c` と無次元パラメータ `ϵ` と `μ`、メッシュサイズ `L` とコレクションポイントの数 `N` を含む問題のパラメータ;

## キーワード（オプション）

  * `guess :: Vector{Real}`: 表面変形の初期推測（提供されていない場合、KdVの正確な式が使用されます）;
  * `x₀ :: Real`: 孤立波の中心（推測が提供されていない場合）;
  * `iterative :: Bool`: `true` の場合はGMRESを通じてヤコビ行列を反転し、`false` の場合はLU分解を使用します;
  * `verbose :: Bool`: `true` の場合は各ステップで数値誤差を印刷します;
  * `max_iter :: Int`: ニュートンアルゴリズムの最大反復回数;
  * `tol :: Real`: 一般的な許容誤差（デフォルトは `1e-10`）;
  * `ktol :: Real`: Krasnyフィルタの許容誤差（デフォルトは `0`、すなわちフィルタリングなし）;
  * `gtol :: Real`: GMRESアルゴリズムの相対許容誤差（デフォルトは `1e-10`）;
  * `dealias :: Int`: Orliczルールによるディーリアリング `1-dealias/(dealias+2)`（デフォルトは `0`、すなわちディーリアリングなし）;
  * `q :: Real`: 修正されたニュートンアルゴリズム

`u_{n+1}=q*u_{n+1}+(1-q)*u_n`（デフォルトは `1`）;

  * `α :: Real`: ヤコビ行列にカーネルへのスペクトル射影を `α` 倍追加します;
  * `KdV :: Bool`: `true` の場合はWhithamの代わりにKdV孤立波を計算します。

# 戻り値

`(u,mesh)` で

  * `u :: Vector{Float64}`: 解;
  * `mesh :: Mesh`: メッシュコレクションポイント。
