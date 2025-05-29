```
BottomHolePressureTarget(q, phase)
```

ボトムホール圧力（bhp）ターゲットで、ターゲット圧力値 `bhp` を持ちます。bhp 制約の下で運転されている井戸は、他の制約（例えば、注入井戸として宣言されたときに井戸が注入から生産に切り替わるなど）に違反しない限り、この値でボトムホール（通常は穿孔の上部）の井戸圧を固定します。

# 例

```julia-repl
julia> BottomHolePressureTarget(100e5)
BottomHolePressureTarget with value 100.0 [bar]
```
