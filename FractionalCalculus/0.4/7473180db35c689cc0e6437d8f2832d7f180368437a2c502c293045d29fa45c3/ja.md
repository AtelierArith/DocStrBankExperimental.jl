# カプート意味の分数導関数

```
fracdiff(f::Function, α, start_point, end_point, step_size, ::Caputo)
```

### 例:

```julia-repl
julia> fracdiff(x->x^5, 0.5, 0, 2.5, 0.0001, CaputoDirect())
```

タプル（**result**, **error**）を返します。これは、この導関数の値が141.59714979764541であり、誤差推定が1.1532243848672914e-6であることを意味します。

[カプート導関数](https://en.wikipedia.org/wiki/Fractional_calculus#Caputo_fractional_derivative)を参照してください。

!!! note
    `Caputo Direct`アルゴリズムは直接計算に属し、精度が保証されますが、より多くのメモリ割り当てを引き起こし、コンパイル時間が長くなる可能性があります。


直接的な数学的表現を使用すると:

$$
^CD_t^α=\frac{1}{\Gamma(n-α)}\int_0^t\frac{f^{(n)}(τ)}{(t-τ)^{α+1-n}}
$$

積分内の導関数については、**複素ステップ微分**を使用して、より正確な値を得ます。
