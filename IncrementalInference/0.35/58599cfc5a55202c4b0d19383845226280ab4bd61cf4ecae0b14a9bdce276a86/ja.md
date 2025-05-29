```julia
mutable struct MetaBayesTree <: IncrementalInference.AbstractBayesTree
```

与えられた `::AbstractDFG` から構築され、推論に使用されるベイズ（ジャンクション）ツリーのデータ構造。
