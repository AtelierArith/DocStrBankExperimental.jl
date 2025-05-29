```
varfinite(A; kwargs...)
```

`A`の分散を計算し、非有限値は無視します。

サポートされている`kwargs`は`sum(f, A; kwargs...)`のものです。

!!! note
    この関数は、入力配列がRGB画像の場合、驚くべき結果を生じることがあります。より明確にするために、実装は`varfinite(img) ≈ varfinite(RGB.(img))`が任意のグレースケール画像に対して成り立つようにされています。詳細については、https://github.com/JuliaGraphics/ColorVectorSpace.jl#abs-and-abs2を参照してください。

