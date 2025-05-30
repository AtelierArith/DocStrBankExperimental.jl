```
integrated_interaction([t,] x, W, ys[, dens_diff])
```

$$
-(W' * \rho)(t, x) = -(W * \rho')(t,x)
$$

を計算します。ここで、$\rho$は粒子`ys`に関連する区分定数密度です。

`t`が省略されると、`W(x)`は時間に依存しないと見なされます。

!!! note
    計算の正確性を確保するために、`dens_diff`は`diff(pwc_density(ys))`と一致しなければなりません。再利用を可能にするために、事前に計算して明示的に渡すことができます（最適化として）。


[`sampled_interaction`](@ref)や[`compute_interaction`](@ref)も参照してください。
