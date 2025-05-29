```
struct AdaptiveReduction{A,B,R<:DirectReduction{A,B}} <: GreedyReduction{A,B}
  reduction::R
  adaptive_nparams::Int
  adaptive_tol::Float64
  adaptive_maxiter::Int
end
```

まだ実装されていません。パラメータ適応型の貪欲削減アルゴリズムとして機能します。
