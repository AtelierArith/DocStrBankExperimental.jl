```
BackwardsKaiserBesselKernel <: AbstractKernel
BackwardsKaiserBesselKernel([β])
```

逆向きの[Kaiser–Bessel](https://en.wikipedia.org/wiki/Kaiser_window#Definition) (KB) スプレッディングカーネルを表します。

このカーネルは基本的に、[`KaiserBesselKernel`](@ref) スプレッディング関数とそのフーリエ変換を入れ替えることによって得られます。Kaiser–Besselカーネルと非常に似た特性を持っています。

# 定義

$$
ϕ(x) = \frac{\sinh \left(β \sqrt{1 - x²} \right)}{π \sqrt{1 - x²}}
\quad \text{ for } |x| ≤ 1
$$

ここで、$β$ は形状因子です。

# フーリエ変換

$$
ϕ̂(k) = I₀ \left( \sqrt{β² - k²} \right)
$$

ここで、$I₀$ は第一種のゼロ次[修正ベッセル関数](https://en.wikipedia.org/wiki/Modified_Bessel_function#Modified_Bessel_functions:_I%CE%B1,_K%CE%B1)です。

# パラメータ選択

デフォルトでは、形状パラメータは[1]に設定されます。

$$
β = γ M π \left( 2 - \frac{1}{σ} \right)
$$

ここで、$M$ はカーネルの半幅、$σ$ はオーバーサンプリング因子です。さらに、$γ = 0.995$ は経験的な「安全係数」であり、FINUFFT [2] で使用されるものと同様に、精度をわずかに向上させます。

このデフォルト値は、明示的に$β$の値を渡すことで上書きできます。

# 実装の詳細

双曲線正弦関数の評価はコストがかかる可能性があるため、このカーネルは正確な区分的多項式近似を介して効率的に評価されます。私たちは、元々FINUFFT [2] のために提案されたのと同じ方法を使用し、後にShamshirgarらによって議論されました[3]。

[1] Potts & Steidl, SIAM J. Sci. Comput. **24**, 2013 (2003)  [2] Barnett, Magland & af Klinteberg, SIAM J. Sci. Comput. **41**, C479 (2019)  [3] Shamshirgar, Bagge & Tornberg, J. Chem. Phys. **154**, 164109 (2021)
