```
transform([S=ComplexF64, ]b1::PositionBasis, b2::FockBasis; x0=1)
transform([S=ComplexF64, ]b1::FockBasis, b2::PositionBasis; x0=1)
```

位置基底とフォック基底の間の変換演算子。

係数は次の関係で結びついています。

$$
ψ(x_i) = \sum_{n=0}^N ⟨x_i|n⟩ ψ_n
$$

ここで、$⟨x_i|n⟩$は、位置$x$における調和トラップポテンシャル内の粒子のn番目の固有状態の値です。すなわち：

$$
⟨x_i|n⟩ = π^{-\frac{1}{4}} \frac{e^{-\frac{1}{2}\left(\frac{x}{x_0}\right)^2}}{\sqrt{x_0}}
            \frac{1}{\sqrt{2^n n!}} H_n\left(\frac{x}{x_0}\right)
$$
