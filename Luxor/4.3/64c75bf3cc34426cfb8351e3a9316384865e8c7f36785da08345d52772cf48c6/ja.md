```
blendmatrix(b::Blend, m)
```

ブレンドの行列を設定します。

ブレンドに一連の行列変換を適用するには：

```julia
A = [1 0 0 1 0 0]
Aj = cairotojuliamatrix(A)
Sj = scalingmatrix(2, .2) * Aj
Tj = translationmatrix(10, 0) * Sj
A1 = juliatocairomatrix(Tj)
blendmatrix(b, As)
```
