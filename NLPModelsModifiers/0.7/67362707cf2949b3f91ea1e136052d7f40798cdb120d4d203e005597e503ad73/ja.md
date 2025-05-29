```
DiagonalAndreiModel(nlp; d0 = fill!(S(undef, nlp.meta.nvar), 1.0))
```

別のタイプのnlpから`DiagonalAndreiModel`を構築します。このとき、ヘッセ行列は対角のアンドレイ準ニュートン演算子を介して近似されます。`d0`はヘッセ行列の対角の初期近似であり、デフォルトでは1のベクトルです。[`DiagonalAndrei演算子のドキュメント`](https://juliasmoothoptimizers.github.io/LinearOperators.jl/stable/reference/#LinearOperators.DiagonalAndrei)を参照してください。
