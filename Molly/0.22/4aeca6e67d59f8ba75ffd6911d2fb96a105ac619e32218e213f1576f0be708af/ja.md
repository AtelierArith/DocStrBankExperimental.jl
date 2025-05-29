```
VelocityVerlet(; <keyword arguments>)
```

速度ヴェルレインテグレーター。

# 引数

  * `dt::T`: シミュレーションの時間ステップ。
  * `coupling::C=NoCoupling()`: シミュレーション中に適用されるカップリング。
  * `remove_CM_motion=1`: このステップ数ごとに重心の運動を除去します。重心の運動を除去しないには、`false`または`0`に設定します。
