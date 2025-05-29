```
obj = heart_phantom(
    circumferential_strain, radial_strain, rotation_angle; 
    heart_rate, asymmetry
)
```

心臓のようなLV 2Dファントム。変数 `circumferential_strain` と `radial_strain` は伸張（正の場合）または収縮（負の場合）に使用されます。`rotation_angle` は回転のためのものです。

# キーワード

  * `circumferential_strain`: (`::Real`, `=-0.3`) 収縮パラメータ。-1から1の間
  * `radial_strain`: (`::Real`, `=-0.3`) 収縮パラメータ。-1から1の間
  * `rotation_angle`: (`::Real`, `=15.0`, `[º]`) 最大回転角
  * `heart_rate`: (`::Real`, `=60`, `[bpm]`) 心拍数
  * `temporal_asymmetry`: (`::Real`, `=0.2`) 収縮が発生する周期の時間割合。したがって、拡張期は `period * (1 - temporal_asymmetry)` の間続きます。

# 戻り値

  * `obj`: (`::Phantom`) 心臓のようなLVファントム構造体
