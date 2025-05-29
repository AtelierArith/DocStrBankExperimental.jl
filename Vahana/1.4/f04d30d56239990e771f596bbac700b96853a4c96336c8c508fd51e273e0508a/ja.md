```
detect_stateless(detect::Bool = true)
```

デフォルトでは、Vahanaは:Statelessヒントが手動で設定されることを期待しています。

この設計上の決定は、ユーザーを混乱させないようにするために行われました。なぜなら、その場合、例えば[`edges`](@ref)が利用できなくなるからです。

この動作は、[`register_edgetype!`](@ref)を呼び出す前に`detect_stateless`を呼び出すことでカスタマイズできます。
