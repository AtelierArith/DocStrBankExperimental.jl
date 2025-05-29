```
integrate(a::TM{T,S}, c0)
integrate(a::TM{TaylorN{T},S}, c0, cc0)
```

独立変数に関して一変数テイラー・モデル（`TaylorModel1`または`RTaylorModel1`）を積分します。`c0`は積分定数で、省略された場合はゼロと見なされます。`a`の係数が`TaylorN`変数である場合、ドメインは`cc0::IntervalBox`によって指定されます。

---

```
integrate(fT, which)
```

`which`変数に関して`fT::TaylorModelN`を積分します。返される`TaylorModelN`は、定積分∫f(x) - ∫f(expansion_point)のテイラー・モデルに対応します。
