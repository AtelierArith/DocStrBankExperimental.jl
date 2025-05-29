```
w_lin(shift, h, time_step; E_r = mean(shift), skip = 0)
```

`E_r`から線形化された式を用いて、`h`時間ステップにわたる再重み付けのための重みを計算します。

$$
w_h^{(n)} = \prod_{j=1}^h [1-dτ(S^{(q+n-j)}-E_r)] ,
$$

ここで、`q = skip`であり、$dτ$は`time_step`です。

[`w_exp`](@ref)、[`growth_estimator`](@ref)、[`mixed_estimator`](@ref)も参照してください。
