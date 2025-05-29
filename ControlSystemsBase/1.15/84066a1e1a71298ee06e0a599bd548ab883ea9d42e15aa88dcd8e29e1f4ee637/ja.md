```
zpk(gain[, Ts])
zpk(num, den, k[, Ts])
zpk(sys)
```

ゼロポールゲイン形式の伝達関数を作成します。分子と分母はそれぞれの極と零点で表されます。

  * `sys::TransferFunction{SisoZpk{T,TR}} = k*numerator/denominator`

ここで、`T`は`k`の型、`TR`は零点/極の型で、通常はFloat64およびComplex{Float64}です。

  * `num`: 分子多項式の根。スカラーまたはベクトルでSISOシステムを作成するか、

またはベクトルの配列でMIMOシステムを作成します。

  * `den`: 分母多項式の根。ベクトルでSISOシステムを作成するか、

またはベクトルの配列でMIMOシステムを作成します。

  * `k`: システムのゲイン。注意、これは`dcgain`とは異なります。
  * `Ts`: 離散時間システムの場合のサンプル時間。

その他の使用法：

  * `zpk(sys)`: `sys`を`zpk`形式に変換します。
  * `zpk("s")`: 伝達関数`s`を作成します。
