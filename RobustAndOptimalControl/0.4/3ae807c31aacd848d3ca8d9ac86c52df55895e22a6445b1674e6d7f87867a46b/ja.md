```
add_output_integrator(sys::StateSpace{<:Discrete}, ind = 1; ϵ = 0)
```

`sys`の出力をインデックス`ind`での出力の積分で増強します。すなわち、`y_aug = [y; ∫y[ind]]`。SISOシステムに積分器と微分器の両方を追加するには、次のようにします。

```julia
Gd = add_output_integrator(add_output_differentiator(G), 1)
```

注意: 数値積分は数値ドリフトの影響を受ける可能性があります。システムの出力が例えば速度参照に対応し、積分が位置参照に対応する場合、このドリフトを軽減する方法を検討してください。
