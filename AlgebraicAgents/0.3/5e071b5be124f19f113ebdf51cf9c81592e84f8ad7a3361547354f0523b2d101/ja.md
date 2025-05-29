```
poke(agent, priority=0[, id])
```

現在の時間ステップでエージェントをポケます。`() -> _interact(agent)`の呼び出しに変換されます。詳細は[`@call`](@ref)を参照してください。

インタラクションは、優先度によってソートされたインスタンス`Opera`内で実装されています。

詳細は[`Opera`](@ref)を参照してください。

# 例

```julia
poke(agent)
poke(agent, 1.) # 優先度が1のとき
```
