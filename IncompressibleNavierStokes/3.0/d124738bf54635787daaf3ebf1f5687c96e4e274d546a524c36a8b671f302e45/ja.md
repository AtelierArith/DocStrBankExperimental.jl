```julia
cosine_grid(a, b, N) -> Any

```

`a`から`b`までの`N + 1`点の非均一グリッドをコサインプロファイルを使用して作成します。すなわち、

$$
x_i = a + \frac{1}{2} \left( 1 - \cos \left( \pi \frac{i}{n} \right) \right)
(b - a), \quad i = 0, \dots, N
$$

[`stretched_grid`](@ref)も参照してください。
