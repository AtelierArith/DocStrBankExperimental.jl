```
@first_stage(def)
```

`stochasticprogram`にファーストステージモデル生成レシピを追加するには、次の構文を使用します。

```julia
@first_stage stochasticprogram::StochasticProgram = begin
    ...
end [defer]
```

ここで、ブロック内ではJuMP構文を使用してファーストステージモデルを定義します。定義中、ファーストステージモデルは`stochasticprogram`の名前に一致する予約語を通じて参照されます。

## 例

次のようにファーストステージモデルを定義します：

$$
  minimize 100x₁ + 150x₂
    s.t  x₁ + x₂ ≤ 120
         x₁ ≥ 40
         x₂ ≥ 20
$$

```julia
@first_stage sp = begin
    @decision(sp, x₁ >= 40)
    @decision(sp, x₂ >= 20)
    @objective(sp, Min, 100*x₁ + 150*x₂)
    @constraint(sp, x₁ + x₂ <= 120)
end
```

参照： [`@second_stage`](@ref)
