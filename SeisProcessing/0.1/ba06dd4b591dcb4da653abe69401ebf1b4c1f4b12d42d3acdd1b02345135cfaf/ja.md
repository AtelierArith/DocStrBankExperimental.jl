```
SeisKolmogoroff(in)
```

波レットをその最小位相同等物に変換します。

# 引数

  * `in::Array{Real,1}`: 入力波レット。

# 例

```julia
julia> using PyPlot
julia> w = Ricker()
julia> wmin = SeisKolmogoroff(w)
julia> plot(w); plot(wmin)
```

# 参考文献

  * Claerbout, Jon F., 1976, Fundamentals of geophysical data processing.

McGraw-Hill Inc.
