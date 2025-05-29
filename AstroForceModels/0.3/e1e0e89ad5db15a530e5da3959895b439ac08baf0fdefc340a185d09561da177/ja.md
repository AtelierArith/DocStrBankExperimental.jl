第三体モデル Astro Model 構造体は、宇宙船に作用する第三体力の加速度を計算するための情報を含みます。

# フィールド

  * `body::CelestialBody`: 宇宙船に作用する天体。
  * `ephem_type::AbstractEphemerisType`: 天体の位置を計算するために使用されるエフェメリスの種類。現在のオプションは Vallado() です。
