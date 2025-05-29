```
AbstractManoptProblem{M<:AbstractManifold}
```

すべての静的（変化しない）特性を持つリーマン最適化問題を説明します。

ここで常に述べるべき最も顕著な特徴は

  * [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$
  * コスト関数 $f:  \mathcal M → ℝ$

通常、コストは[`AbstractManifoldObjective`](@ref)内にあるべきです。
