```
 hreval(Ahr::HarmonicArray, t; ntrunc, exact = true) -> A::Matrix
```

ハーモニック配列 `Ahr` を評価し、連続時間の周期行列 `A(t)` を象徴的な時間値 `t` に対して表します。`A(t)` の象徴的評価が行われます（詳細は [`hr2psm`](@ref）を参照）。キーワード引数 `ntrunc` は評価に使用されるハーモニクスの数を指定します（デフォルト：可能な最大数）。
