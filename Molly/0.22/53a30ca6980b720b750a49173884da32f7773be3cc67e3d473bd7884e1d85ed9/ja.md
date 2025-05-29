```
Langevin(; <キーワード引数>)
```

Langevinインテグレーターは、OpenMMのLangevin Middle Integratorに基づいています。

[Zhang et al. 2019](https://doi.org/10.1021/acs.jpca.9b02771)を参照してください。これはリープフロッグインテグレーターであり、速度は位置の半分の時間ステップだけ遅れています。

# 引数

  * `dt::S`: シミュレーションの時間ステップ。
  * `temperature::K`: シミュレーションの平衡温度。
  * `friction::F`: シミュレーションの摩擦係数。
  * `coupling::C=NoCoupling()`: シミュレーション中に適用されるカップリング。
  * `remove_CM_motion=1`: このステップ数ごとに重心の運動を除去します。重心の運動を除去しない場合は`false`または`0`に設定します。
