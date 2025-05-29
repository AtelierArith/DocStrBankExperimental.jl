# アタンガナ・バレアヌの分数導関数計算をアタンガナ・セダ（ニュートン多項式）法を用いて行う。

```
fracdiff(f::Function, α, start_point, end_point, step_size, ::AtanganaSeda)
```

### 例:

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.0001, AtanganaSeda())
-91.4589645808849
```

### 参考文献

```tex
Fractional Stochastic Differential Equations
```
