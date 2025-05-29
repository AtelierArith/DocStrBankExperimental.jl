```
svdl(A) -> Σ, L, [history]
```

いくつかの特異値（およびオプションでベクトル）を、厚い再起動を伴うゴルブ-カハン-ランチョス二重対角化 [^Golub1965] を使用して計算します [^Wu2000]。

`log` が `true` に設定されている場合、メソッドはタプル `X, L, ch` を出力します。ここで `ch` は `ConvergenceHistory` オブジェクトです。そうでない場合は、`X, L` のみが返されます。

# 引数

  * `A` : 特異値を求める行列または行列のようなオブジェクト。

## キーワード

  * `nsv::Int = 6`: 要求される特異値の数;
  * `v0 = random unit vector`: 行列 `A` の定義域における開始推測ベクトル。`q` の長さは `A` の列数と同じである必要があります;
  * `k::Int = 2nsv`: 再起動前に計算するランチョスベクトルの最大数;
  * `j::Int = nsv`: 再起動の最後に保持するベクトルの数。`j < nsv` は推奨しません;
  * `maxiter::Int = minimum(size(A))`: 実行する最大反復回数;
  * `verbose::Bool = false`: 各反復で情報を印刷;
  * `tol::Real = √eps()`: 各要求された特異値における最大絶対誤差;
  * `reltol::Real=√eps()`: 入力行列の推定ノルムに対する各要求された特異値の最大誤差;
  * `method::Symbol=:ritz`: 使用する再起動アルゴリズム。妥当な選択肢は:

    1. `:ritz`: リッツ値を用いた厚い再起動 [Wu2000]。
    2. `:harmonic`: 調和リッツ値を用いた再起動 [Baglama2005]。
  * `vecs::Symbol = :none`: 返す特異ベクトル。

    1. `:both`: 左右両方の特異ベクトルが返されます。
    2. `:left`: 左の特異ベクトルのみが返されます。
    3. `:right`: 右の特異ベクトルのみが返されます。
    4. `:none`: 特異ベクトルは返されません。
  * `dolock::Bool=false`: `true` の場合、収束したリッツ値をロックし、次のマクロ反復で探索されるクリロフ部分空間から削除します;
  * `log::Bool = false`: メソッド実行の追加情報を含む `ConvergenceHistory` 型の追加要素を出力します。

# 戻り値

**`log` が `false` の場合**

  * `Σ`: `vecs == :none` の場合は要求された特異値のリスト（デフォルト）、そうでない場合は要求された特異ベクトルが埋め込まれた `SVD` オブジェクトを返します;
  * `L`: A の計算された部分因子分解。

**`log` が `true` の場合**

  * `Σ`: `vecs == :none` の場合は要求された特異値のリスト（デフォルト）、

そうでない場合は要求された特異ベクトルが埋め込まれた `SVD` オブジェクトを返します;

  * `L`: A の計算された部分因子分解;
  * `history`: 収束履歴。

**ConvergenceHistory キー**

  * `:betas` => `betas`: 計算されたベータの履歴。
  * `:Bs` => `Bs`: 計算された射影行列の履歴。
  * `:ritz` => `ritzvalhist`: 各反復で計算されたリッツ値。
  * `:conv` => `convhist`: 収束データ。

[^Golub1965]: Golub, Gene, and William Kahan. "Calculating the singular values and pseudo-inverse of a matrix." Journal of the Society for Industrial and Applied Mathematics, Series B: Numerical Analysis 2.2 (1965): 205-224.

[^Wu2000]: Wu, Kesheng, and Horst Simon. "Thick-restart Lanczos method for large symmetric eigenvalue problems." SIAM Journal on Matrix Analysis and Applications 22.2 (2000): 602-616.
