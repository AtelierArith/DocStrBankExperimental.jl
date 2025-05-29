```
DebugMessages <: DebugAction
```

[`AbstractManoptSolverState`](@ref) またはそのサブステップの一つである [`Stepsize`](@ref) は、計算中に警告を生成することがあります。このデバッグは、メッセージのタイプに応じて `:print` したり、 `:info` や `:warnings`、さらには `:error` として表示するために使用できます。

# コンストラクタ

```
DebugMessages(mode=:Info, warn=:Once; io::IO=stdout)
```

メッセージデバッグを特定の `mode` に初期化します。利用可能なモードは次のとおりです。

  * `:Error`:   メッセージをエラーとして発行し、発生する問題で停止します
  * `:Info`:    メッセージを `@info` として発行します
  * `:Print`:   メッセージをストリーム `io` に印刷します
  * `:Warning`: メッセージを警告として発行します

`warn` レベルは `:Once` に設定すると最初のメッセージのみを表示し、 `:Always` に設定するとすべてのメッセージを報告します。 `:No` に設定するとこれを無効にし、この [`DebugAction`](@ref) は非アクティブになります。他のすべてのシンボルは `:Always` として扱われます。
