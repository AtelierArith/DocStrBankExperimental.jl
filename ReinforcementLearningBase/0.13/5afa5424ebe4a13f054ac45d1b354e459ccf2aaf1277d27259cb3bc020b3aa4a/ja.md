```
plan!(π::AbstractPolicy, env) -> action
```

ポリシーは強化学習における最も基本的な概念です。ここでは、エージェントのアクションは、環境とポリシーを受け取りアクションを返す`plan!`によって決定されます。

!!! note
    なぜ入力を`AbstractEnv`として定義するのか疑問に思っている場合は、[こちら](https://github.com/JuliaReinforcementLearning/ReinforcementLearning.jl/issues/86)の議論を参照してください。


!!! warning
    ポリシー`π`は内部状態を変更する可能性がありますが、`env`を変更してはいけません。本当に必要な場合は、元の`env`を変更しないように`env`のコピーを作成することを忘れないでください。

