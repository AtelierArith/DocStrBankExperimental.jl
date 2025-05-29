ガウスショックを仮定したシミュレーションサンプルパスを計算します。

##### 引数

  * `arma::ARMA`: `ARMA`型のインスタンス
  * `;ts_length::Integer(90)`: シミュレーションの長さ
  * `;impulse_length::Integer(30)`: インパルス応答を計算するためのホライズン（`impulse_response`のドキュメントも参照）

##### 戻り値

  * `X::Vector{Float64}`: ARMAモデル`arma`のシミュレーション
