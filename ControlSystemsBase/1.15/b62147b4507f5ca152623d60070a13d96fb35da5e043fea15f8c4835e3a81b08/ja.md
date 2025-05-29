```
sys = tf(num, den[, Ts])
sys = tf(gain[, Ts])
```

多項式の分数として作成します：

  * `sys::TransferFunction{SisoRational{T,TR}} = numerator/denominator`

ここで、Tは多項式の係数の型です。

  * `num`: 分子多項式の係数。スカラーまたはベクトルでSISOシステムを作成するか、

またはベクトルの配列でMIMOシステムを作成します。

  * `den`: 分母多項式の係数。ベクトルでSISOシステムを作成するか、

またはベクトルの配列でMIMOシステムを作成します。

  * `Ts`: 離散時間システムの場合のサンプル時間。

多項式の係数は、最高次の項から順に並べられます。

その他の使用法：

  * `tf(sys)`: `sys`を`tf`形式に変換します。
  * `tf("s")`, `tf("z")`: 連続時間伝達関数`s`または離散時間伝達関数`z`を作成します。
  * `numpoly(sys)`, `denpoly(sys)`: `sys`の分子と分母の多項式をベクトルの行列として取得します。外側の行列のサイズは`n_output × n_inputs`です。

参照：[`zpk`](@ref), [`ss`](@ref)。
