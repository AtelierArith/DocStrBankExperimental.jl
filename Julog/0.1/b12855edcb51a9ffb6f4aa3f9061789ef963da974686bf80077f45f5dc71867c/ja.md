```
derive(goals, clauses; <keyword arguments>)
fwd_chain(goals, clauses; <keyword arguments>)
```

初期の節のセットから前向き連鎖を介して目標を導出します。

# 引数

  * `goals::Vector{<:Term}`: 証明またはクエリを行うためのJulog用語のリスト。
  * `clauses::Vector{Clause}`: Julogの節のリスト。
  * `max-steps::Real=100`: 失敗で終了する前の最大ステップ数。

他のサポートされている引数については`resolve`を参照してください。
