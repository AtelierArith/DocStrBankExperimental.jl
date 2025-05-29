```
add_differentiator(sys::StateSpace{<:Discrete})
```

`sys`の出力に数値的差分（離散時間導関数）を追加します。すなわち、`y_aug = [y; (y-y_prev)/sys.Ts]` SISOシステムに積分器と微分器の両方を追加するには、次のようにします。

```julia
Gd = add_output_integrator(add_output_differentiator(G), 1)
```
