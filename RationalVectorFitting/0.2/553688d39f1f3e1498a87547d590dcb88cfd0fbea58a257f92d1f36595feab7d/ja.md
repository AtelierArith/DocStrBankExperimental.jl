```
residue_identification(s, f, poles, weight) -> residues, d, h
```

ベクトルフィッティングのステージ2。`ndims(f) == 2` のとき、`f` と `weight` の各列に対して別々に呼び出す必要があります。

関連情報として [`vector_fitting`](@ref)、[`pole_identification`](@ref) を参照してください。
