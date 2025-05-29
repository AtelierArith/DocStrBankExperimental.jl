```
Average(field::AbstractField; dims=:, condition=nothing, mask=0)
```

`field`の空間平均を`dims`にわたって表す`Reduction`を返します。

定期的に間隔を空けた次元では、これは数値的な`mean!`に相当します。

間隔が変動する次元では、`field`は適切なグリッドの長さ、面積、または体積で乗算され、区間の全体的な空間の広がりで除算されます。

`condition`および`mask`キーワード引数を使用した情報と例については、[`ConditionalOperation`](@ref Oceananigans.AbstractOperations.ConditionalOperation)を参照してください。
