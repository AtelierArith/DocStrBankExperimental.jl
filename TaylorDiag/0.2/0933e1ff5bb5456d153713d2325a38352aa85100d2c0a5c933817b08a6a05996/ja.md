```
COR(Cr::AbstractArray,C::AbstractArray)
```

参照コレクション Cr と C の間の相関係数を計算します。注意: この関数は数値誤差のため、1.0 と式の最小値を正確に返します。

```julia
Cr = [1.0, 2.0, 3.0]
C  = [1.0, 2.0, 3.0]
Correlation = sum( (C.-mean(C)) .* (Cr.-mean(Cr)) ) ./ (length(C) .* STD(C) .* STD(Cr))
```

この場合、`correlation=1.0000000000000002`、または `correlation=1+2e-16` であり、(1/3)（およびその倍数）の丸めによる計算誤差です。
