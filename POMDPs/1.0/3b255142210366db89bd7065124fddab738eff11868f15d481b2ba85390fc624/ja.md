```
initialize_belief(updater::Updater,
                     state_distribution::Any)
initialize_belief(updater::Updater, belief::Any)
```

`updater`を使用して更新可能な信念を返します。この信念は`state_distribution`または`belief`と類似の分布を持ちます。

変換は損失を伴う場合があります。この関数は冪等性も持ちます。すなわち、すでに正しい型である場合、信念をそのまま通すデフォルトの実装があります：`initialize_belief(updater::Updater, belief) = belief`
