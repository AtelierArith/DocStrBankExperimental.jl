```
GroundAction(name, term, preconds, effect)
```

グラウンドアクションの定義であり、対応するアクションスキーマの`name`、グラウンド引数を持つ`term`、`preconds`のリスト、および[`PDDL.GenericDiff`](@ref)または[`PDDL.ConditionalDiff`](@ref)として表される`effect`で構成されています。
