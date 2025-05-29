```
par(t::TPS, monomialindex)
```

指定された単項式を含むTPSから多項式を抽出し、単項式を削除します。単項式を指定するために、3つの単項式インデックス方式（順序による、スパース単項式による、または単項式インデックスによる - 詳細についてはGTPSAマニュアルの単項式インデクシングセクションを参照）を使用できます。

# 例: 変数/パラメータインデックス:

```julia-repl
julia> d = Descriptor(5, 10, 2, 10); Δx = @vars(d); Δk = @params(d);

julia> f = 2*Δx[1]^2*Δx[3] + 3*Δx[1]^2*Δx[2]*Δx[3]*Δx[4]^2*Δx[5]*Δk[1] + 6*Δx[3] + 5
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  5.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  6.0000000000000000e+00      1      0   0   1   0   0   |   0   0
  2.0000000000000000e+00      3      2   0   1   0   0   |   0   0
  3.0000000000000000e+00      8      2   1   1   2   1   |   1   0


julia> par(f, 3)
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  6.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  2.0000000000000000e+00      2      2   0   0   0   0   |   0   0
  3.0000000000000000e+00      7      2   1   0   2   1   |   1   0


julia> par(f, param=1)
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  3.0000000000000000e+00      7      2   1   1   2   1   |   0   0
```

# 例: 単項式インデックス - 順序による

```julia-repl
julia> par(f, [2,:,1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  3.0000000000000000e+00      5      0   1   0   2   1   |   1   0


julia> par(f, [2,0,1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0   0   0   0   |   0   0
```

# 例: 単項式インデックス - スパース単項式による

```julia-repl
julia> par(f, [1=>2, 3=>1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  3.0000000000000000e+00      5      0   1   0   2   1   |   1   0


julia> par(f, params=[1=>1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  3.0000000000000000e+00      7      2   1   1   2   1   |   0   0
```
