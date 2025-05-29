```
deriv(t1::TPS, monomialindex)
∂(t1::TPS, monomialindex)
```

変数/パラメータインデックスで指定された変数/パラメータに関して `t1` を微分するか、または順序によるインデックス指定またはスパースモノミアルによるインデックス指定で指定された任意のモノミアルを微分します。

# 例: 変数/パラメータインデックス:

```julia-repl
julia> d = Descriptor(2, 5);

julia> Δx = @vars(d);

julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], 1)
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      0   1


julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], 2)
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      1   0
```

# 例: モノミアルインデックスによる順序指定

```julia-repl
julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [1,0])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      0   1


julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [1,1])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  3.0000000000000000e+00      0      0   0
```

# 例: スパースモノミアルによるモノミアルインデックス

```julia-repl
julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [1=>1])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      0   1


julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [2=>1])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      1   0
```
