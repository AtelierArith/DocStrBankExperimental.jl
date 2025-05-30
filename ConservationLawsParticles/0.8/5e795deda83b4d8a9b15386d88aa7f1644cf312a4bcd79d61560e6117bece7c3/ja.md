```
sampled_interaction([t,] x, W′, ys)
```

$$
-(W' * \dot\rho)(t, x)
$$

を計算します。これは、$-(W' * \rho)(t, x)$のサンプリングされた近似であり、ここで$\rho$は粒子`ys`に関連する区分定数密度です。

`t`が省略されると、`W′(x)`は時間に依存しないと見なされます。

[`integrated_interaction`](@ref)や[`compute_interaction`](@ref)も参照してください。
