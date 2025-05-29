```
DebugGradient <: DebugAction
```

現在の反復で評価された勾配のデバッグ

# コンストラクタ

```
DebugGradient(; long=false, prefix= , format= "$prefix%s", io=stdout)
```

勾配の短い（`false`）または長い（`true`）デフォルトテキストを表示するか、`prefix`を手動で設定します。あるいは、完全なフォーマットを設定することもできます。
