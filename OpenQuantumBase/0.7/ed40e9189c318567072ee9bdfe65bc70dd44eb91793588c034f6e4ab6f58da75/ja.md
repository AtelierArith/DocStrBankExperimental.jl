```julia
eigen_decomp(H, s; lvl, kwargs...)

```

ハミルトニアン `H` の固有値分解を時間点の配列 `s` で計算します。出力は最も低い `lvl` の固有状態とそれに対応する固有値を保持します。出力 `(vals, vecs)` の次元はそれぞれ `(lvl, length(s))` と `(size(H, 1), lvl, length(s))` です。
