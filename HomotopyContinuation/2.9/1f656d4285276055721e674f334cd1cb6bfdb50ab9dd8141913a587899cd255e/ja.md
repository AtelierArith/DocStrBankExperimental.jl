```
total_degree_start_solutions(degrees)
```

システムのスタートソリューションのイテレータを返します

$$
\begin{array}{rl}
    z_1^{d_1} - 1 &= 0 \\
    z_2^{d_2} - 1 &= 0 \\
    &\vdots \\
    z_n^{d_n} - 1 &= 0 \\
\end{array}
$$

ここで $d_i$ は `degrees[i]` です。

## 例

```julia-repl
julia> iter = total_degree_start_solutions([2, 2])
4 total degree start solutions for degrees [2, 2]

julia> collect(iter)
4-element Array{Array{Complex{Float64},1},1}:
 [1.0 + 0.0im, 1.0 + 0.0im]
 [-1.0 + 1.2246467991473532e-16im, 1.0 + 0.0im]
 [1.0 + 0.0im, -1.0 + 1.2246467991473532e-16im]
 [-1.0 + 1.2246467991473532e-16im, -1.0 + 1.2246467991473532e-16im]
```
