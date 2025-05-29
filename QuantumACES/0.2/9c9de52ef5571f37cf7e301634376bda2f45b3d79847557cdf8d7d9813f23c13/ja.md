```
get_eigenvalues(d::Design)
get_eigenvalues(d::Design, gate_eigenvalues::Vector{Float64})
```

デザイン `d` の回路固有値を返し、オプションでゲート固有値 `gate_eigenvalues` を使用します。
