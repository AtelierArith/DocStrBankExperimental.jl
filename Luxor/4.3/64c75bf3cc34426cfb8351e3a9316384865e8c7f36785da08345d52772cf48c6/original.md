```
blendmatrix(b::Blend, m)
```

Set the matrix of a blend.

To apply a sequence of matrix transforms to a blend:

```julia
A = [1 0 0 1 0 0]
Aj = cairotojuliamatrix(A)
Sj = scalingmatrix(2, .2) * Aj
Tj = translationmatrix(10, 0) * Sj
A1 = juliatocairomatrix(Tj)
blendmatrix(b, As)
```
