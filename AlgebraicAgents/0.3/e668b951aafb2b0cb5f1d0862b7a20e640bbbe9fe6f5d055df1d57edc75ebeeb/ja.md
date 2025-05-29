```
wiring_diagram(agent; parentship_edges=true, wires=true)
wiring_diagram(agents; parentship_edges=true, wires=true)
wiring_diagram(groups; group_labels=nothing, parentship_edges=true, wires=true)
```

エージェントの階層を示すGraphvizグラフをレンダリングします。デフォルトでは、グラフは親エージェントと子エージェントの間のエッジと注釈付きのワイヤを表示します。

また、[`agent_hierarchy_mmd`](@ref)も参照してください。

# 例

```julia
# 複合問題を構築します。
joint_system = ⊕(alice, bob, name = "joint system")

wiring_diagram(joint_system)

# 親と子の間のエッジを表示しない。
wiring_diagram(joint_system; parentship_edges=false)

# リストされたエージェントのみを表示します。
wiring_diagram([alice, alice1, bob, bob1])

# エージェントを2つのクラスターにグループ化します。
wiring_diagram([[alice, alice1], [bob, bob1]])
# クラスターにラベルを提供します。
wiring_diagram([[alice, alice1], [bob, bob1]]; group_labels=["alice", "bob"], parentship_edges=false)
```
