```
IterControl{S}
IterControl(n::Int, base::Int, masks, factors) -> IterControl
```

制御された部分空間を反復するためのイテレータです。詳細は[`itercontrol`](@ref)を参照してください。`S`はチャンクの数、`n`はヒルベルト空間のサイズ、`base`はカウンタの基数、`masks`と`factors`はターゲットヒルベルト空間を列挙するためのヘルパーです。
