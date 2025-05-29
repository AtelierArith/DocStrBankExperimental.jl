```
node_densities(cell_positions::AbstractVector{T}; smooth_boundary=true) where {T<:Number}
```

セルの位置からセル密度を計算し、各ノードに密度を割り当てます。`smooth_boundary`がtrueの場合、

$$
q_i(t) = \begin{cases} \dfrac{2}{x_2(t)-x_1(t)} - \dfrac{2}{x_3(t)-x_1(t)} & i=1, \\[6pt]
\dfrac{2}{x_{i+1}(t)-x_{i-1}(t)} & i=2,\ldots,n-1, \\[6pt]
\dfrac{2}{x_n(t) - x_{n-1}(t)} - \dfrac{2}{x_n(t)-x_{n-2}(t)} & i=n. \end{cases}
$$

そうでない場合、

$$
q_i(t) = \begin{cases} \dfrac{1}{x_2(t)-x_1(t)} & i=1, \\[6pt]
\dfrac{2}{x_{i+1}(t)-x_{i-1}(t)} & i=2,\ldots,n-1, \\[6pt]
\dfrac{1}{x_n(t) - x_{n-1}(t)} & i=n. \end{cases}
$$

各ノードではなく各セルの密度の推定値が必要な場合は、[`cell_densities`](@ref)を参照してください。
