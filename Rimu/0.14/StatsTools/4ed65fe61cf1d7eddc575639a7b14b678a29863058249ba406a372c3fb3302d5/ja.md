```
growth_witness(shift::AbstractArray, norm::AbstractArray, dt, [b]; skip=0)
```

成長ウィットネスを計算します

$$
G^{(n)} = S^{(n)} - \frac{\vert\mathbf{c}^{(n+1)}\vert -
          \vert\mathbf{c}^{(n)}\vert}{\vert\mathbf{c}^{(n)}\vert d\tau},
$$

ここで `S` は `shift` であり、$\vert\mathbf{c}^{(n)}\vert ==$ `norm[n, 1]` です。`b ≥ 1` を設定すると、[`smoothen()`](@ref) を使用して `b` タイムステップのスライディング平均が計算されます。最初の `skip` タイムステップはスキップされます。`mean(growth_witness)` は、`h=0` の [`growth_estimator`](@ref) とほぼ同じです。

また、[`growth_estimator`](@ref) も参照してください。
