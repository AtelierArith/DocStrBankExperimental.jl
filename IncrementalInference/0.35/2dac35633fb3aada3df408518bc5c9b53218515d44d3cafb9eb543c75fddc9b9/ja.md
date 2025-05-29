```julia
defaultFixedLagOnTree!(dfg; ...)
defaultFixedLagOnTree!(dfg, len; limitfixeddown)

```

ツリー上でスマートメッセージパッシングを使用して、固定遅延のような操作のデフォルトを有効にします。

ノート：

  * これらはデフォルト設定に過ぎず、各使用ケースシナリオで変更可能です。
  * デフォルトは、ツリーの葉までダウンソルブを更新しません。
