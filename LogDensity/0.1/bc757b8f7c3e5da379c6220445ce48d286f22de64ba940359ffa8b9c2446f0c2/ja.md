```
(logf, β) = logdensity( X, x, h; 様々なオプション引数 )

データベクター X の対数密度とその導関数の推定値を、バンド幅 h を使用してベクター x の要素で評価します。タプル ( logf, β ) を返し、ここで logf は評価点に対応する要素を持つベクターであり、β は評価点に対応する行と導関数に対応する列を持つ行列です; S = 1 の場合でもこの行列です。
```

# 必須引数

  * `X::Vector{T}`: データのベクター
  * `x::Vector{T}`: 評価点のベクター
  * `h::T`: バンド幅

T は浮動小数点型です。

# オプション引数

  * `g::Function=g`: 使用する関数 g (Pinkse と Schurter を参照)
  * `dg::Function=dg`: その導関数
  * `S::Int=1`: 計算する導関数の数
  * `minx::T=0.0`: サポートの左側
  * `maxx::T=Inf`: サポートの右側
  * `logf::Bool=true`: 対数密度自体を計算するかどうか
  * `mz::Function=LogDensity.epanechnikov`: 対数密度自体に使用するカーネル
  * `anal::Bool=true`: 多くのサニティチェックを実行するかどうか

カーネルの他の選択肢は:  LogDensity.quartic LogDensity.gaussian LogDensity.triweight LogDensity.uniform LogDensity.cosinus
