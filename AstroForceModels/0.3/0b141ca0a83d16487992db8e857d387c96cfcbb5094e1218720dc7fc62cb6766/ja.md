CelestialBodyのエフェメリス位置をThirdBodyModelで計算する便利さ get_position()をラップします。

# 引数

  * `time::Number`: シミュレーションの現在の時間（秒単位）。

# 戻り値

  * `body_position: SVector{3}`: J2000フレームにおける3次元の第三者の位置。
