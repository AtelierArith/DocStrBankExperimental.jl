```julia
combine_turn_statistics(trajectory, x, y)

```

軌跡に関するターン統計を結合します。実装は、ターン統計に対応する木が同じ順序であると仮定できます。次のとき

```julia
τ = combine_turn_statistics(trajectory, τ₁, τ₂)
is_turning(trajectory, τ)
```

結合されたターン統計 `τ` は呼び出し元から逃げないことが保証されているため、例えば型を変更することができます。

# 例

```julia

```
