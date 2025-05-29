```
statistics(
    targetind::Int,
    parents::AbstractVector{Int},
    ncategories::AbstractVector{Int},
    data::AbstractMatrix{Int}
    )
```

は、ターゲット変数の十分統計量テーブルを出力します。このテーブルは r × q の形をしており、r = ncategories[i] は変数のインスタンシエーションの数、q は変数 i の親のインスタンシエーションの数です。

r 値は 1 → ncategories[i] の順に並べられています。q 値は Julia Base の ind2sub() と同じ順序で並べられています。したがって、最初の親のインスタンシエーション（parents[i] で与えられた順序による）は最も早く変化します。

例: 変数 1 は親 2 と 3 を持ち、r₁ = 2, r₂ = 2, r₃ = 3 です。変数 1 の q は q = r₂×r₃ = 6 です。N は 6×2 の行列で、次のようになります:          N[1,1] は v₁ = 1, v₂ = 1, v₃ = 1 の回数          N[2,1] は v₁ = 1, v₂ = 2, v₃ = 1 の回数          N[3,1] は v₁ = 1, v₂ = 1, v₃ = 2 の回数          N[4,1] は v₁ = 1, v₂ = 2, v₃ = 2 の回数          N[5,1] は v₁ = 1, v₂ = 1, v₃ = 3 の回数          N[6,1] は v₁ = 1, v₂ = 2, v₃ = 3 の回数          N[6,2] は v₁ = 2, v₂ = 1, v₃ = 1 の回数          ...
