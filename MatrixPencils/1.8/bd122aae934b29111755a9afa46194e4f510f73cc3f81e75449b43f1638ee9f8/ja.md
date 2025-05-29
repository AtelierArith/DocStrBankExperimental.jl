```
eigselect1(ev, sdeg, evref, disc; cflag) -> (γ, evupd)
```

与えられた固有値のセットから、ベクトル `ev` で割り当てる実数または複素数の固有値 `γ` を選択します。結果の `evupd` には `ev` からの残りの固有値が含まれます。選択された固有値 `γ` は、参照値 `evref` に最も近いものです。もし `ev = missing` で `disc = false` の場合、`cflag = false`（実数の場合）なら `γ` は希望する安定度 `sdeg` に等しく設定され、`cflag = true`（複素数の場合）なら `γ` は `γ = sdeg + im*imag(evref)` に設定されます。もし `ev = missing` で `disc = true` の場合、`cflag = false`（実数の場合）なら `γ` は希望する安定度 `sdeg` に等しく設定され、`cflag = true`（複素数の場合）なら `γ` は `γ = (sdeg/abs(evref))*evref` に設定されます。もし `ev = missing` で `sdeg = missing` の場合、`γ = nothing` となります。
