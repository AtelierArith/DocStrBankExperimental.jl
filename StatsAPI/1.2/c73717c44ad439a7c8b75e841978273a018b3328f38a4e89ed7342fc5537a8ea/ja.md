```
predict(model::RegressionModel, [newX])
```

`model`の予測応答を形成します。新しい共変量値`newX`を供給することができ、これは`model`をフィットさせるために使用されたものと同じタイプと構造である必要があります。例えば、GLMの場合、一般的には元の予測因子と同じ変数名を持つ`DataFrame`になります。
