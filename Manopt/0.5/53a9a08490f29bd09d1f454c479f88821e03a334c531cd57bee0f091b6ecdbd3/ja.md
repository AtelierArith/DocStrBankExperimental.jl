```
DebugGradientNorm <: DebugAction
```

現在の反復で評価された勾配のデバッグ。

# コンストラクタ

```
DebugGradientNorm([long=false,p=print])
```

勾配ノルムの短い（`false`）または長い（`true`）デフォルトテキストを表示します。

```
DebugGradientNorm(prefix[, p=print])
```

勾配ノルムの前に`prefix`を表示します。
