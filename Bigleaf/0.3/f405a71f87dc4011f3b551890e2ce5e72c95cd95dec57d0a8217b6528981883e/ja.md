```
Monin_Obukhov_length(Tair, pressure, ustar, H; constants)
Monin_Obukhov_length!(df;constants=BigleafConstants())
Monin_Obukhov_length(df;constants=BigleafConstants())
```

モニン-オブコフ長を計算します。

# 引数

  * `Tair`      : 空気温度 (℃)
  * `pressure`  : 大気圧 (kPa)
  * `ustar`     : 摩擦速度 (m s-1)
  * `H`         : 感覚熱フラックス (W m-2)
  * `df`        : 上記の変数を含むデータフレーム

オプション

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書 

      * `Kelvin` - 摂氏からケルビンへの変換
      * `cp` - 定圧の空気の比熱 (J K-1 1)
      * `k` - ボン・カルマン定数 (-)
      * `g` - 重力加速度 (m s-2)

# 詳細

モニン-オブコフ長 (L) は次のように与えられます：

$$
L = - (\rho * cp * ustar^3 * Tair) / (k * g * H)
$$

ここで、$\rho$ は空気密度 (kg m-3) です。

# 注意

Lは非常に低いustar値に対して非常に小さくなることに注意してください。これはLを入力として使用する後続の関数に影響を与えます。データをフィルタリングし、低いustar値 (ustar < ~0.2) を事前に除外することをお勧めします。

# 値

モニン-オブコフ長 L (m)。非変異データフレームバリアントはベクトルを返し、変異バリアントは列 `:MOL` を追加または修正します。

# 参考文献

Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany. 

# 参照

[`stability_parameter`](@ref)

```@example; output = false
Monin_Obukhov_length(
  Tair=25,pressure=100,
  ustar=seq(0.2,1,0.1),H=seq(40,200,20))
```
