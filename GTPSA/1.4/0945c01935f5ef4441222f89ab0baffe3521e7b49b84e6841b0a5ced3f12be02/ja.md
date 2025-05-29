```
mono([tpstype, ] monomialindex [, use=(descriptor|tps)])
```

指定された単項式を1に設定した`TPS`を返します。`tpstype`のデフォルトは`TPS{Float64,GTPSA.Dynamic}`です。単項式を1に設定するために、3つの単項式インデックス方式（順序による、スパース単項式、または単項式インデックス - 詳細はGTPSAマニュアルの単項式インデックスセクションを参照）を使用できます。例えば、この関数への呼び出しは、`t = (tpstype)(use=use); t[monomialindex] = 1`を実行するのと同等です。

`use`は、`tpstype <: TPS{T where {T},<:GTPSA.Dynamic}`の場合にのみ指定できます。

# 例: 変数/パラメータインデックス:

```julia-repl
julia> d = Descriptor(3,10,2,10);

julia> mono(1)
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      1   0   0   |   0   0


julia> mono(ComplexTPS64, 1)
ComplexTPS64{GTPSA.Dynamic}:
 Real                     Imag                       Order   Exponent
  1.0000000000000000e+00   0.0000000000000000e+00      1      1   0   0   |   0   0


julia> mono(ComplexTPS64{d}, param=2)
ComplexTPS64{Descriptor(NV=3, MO=10, NP=2, PO=10)}:
 Real                     Imag                       Order   Exponent
  1.0000000000000000e+00   0.0000000000000000e+00      1      0   0   0   |   0   1
```

# 例: 単項式インデックス - 順序による

```julia-repl
julia> mono([1,2,3])
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      6      1   2   3   |   0   0


julia> mono([0,0,3,2,1], use=d)
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      6      0   0   3   |   2   1


julia> mono(TPS64{d}, [1,0,0,0,1])
TPS64{Descriptor(NV=3, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      2      1   0   0   |   0   1
```

# 例: 単項式インデックス - スパース単項式による

```julia-repl
julia> mono([1=>1])
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      1   0   0   |   0   0


julia> mono([2=>1])
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      0   1   0   |   0   0


julia> mono([1=>1], params=[2=>1], use=d)
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      2      1   0   0   |   0   1
```
