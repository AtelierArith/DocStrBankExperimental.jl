`SinewaveGenerator`を次の形式の出力で構築します

$$
    x(t) = A sin(2 \pi f  (t - \tau) + \phi) + B
$$

ここで、$A$は`amplitude`、$f$は`frequency`、$\tau$は`delay`、$\phi$は`phase`、$B$は`offset`です。

# フィールド

  * `amplitude::Real`: 振幅
  * `frequency::Real`: 周波数
  * `phase::Real`: 位相
  * `delay::Real`: 秒単位の遅延
  * `offset::Real`: オフセット
  * `output::Causal.Outport`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
