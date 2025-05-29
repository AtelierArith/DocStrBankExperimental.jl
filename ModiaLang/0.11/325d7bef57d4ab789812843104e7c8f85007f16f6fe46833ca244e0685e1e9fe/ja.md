```
get_lastValue(model::SimulationModel, name::String; unit=true)
```

変数 `name` の最後に保存された値を `model` から返します。`unit=true` の場合は単位付きの値を返し、そうでない場合は単位を取り除いた値を返します。

`name` が不明であるか、まだ結果値が利用可能でない場合は、情報メッセージが表示され、関数は `nothing` を返します。
