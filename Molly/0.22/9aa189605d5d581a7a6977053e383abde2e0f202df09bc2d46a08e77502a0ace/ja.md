```
OverdampedLangevin(; <keyword arguments>)
```

オーバーダンプされたランジュバン方程式をオイラー・マルヤマ法を使用してシミュレートします。

現在、制約には対応しておらず、警告を表示して制約を適用せずに続行します。

# 引数

  * `dt::S`: シミュレーションの時間ステップ。
  * `temperature::K`: シミュレーションの平衡温度。
  * `friction::F`: シミュレーションの摩擦係数。
  * `remove_CM_motion=1`: このステップ数ごとに重心の運動を除去します。重心の運動を除去しないには、`false`または`0`に設定します。
