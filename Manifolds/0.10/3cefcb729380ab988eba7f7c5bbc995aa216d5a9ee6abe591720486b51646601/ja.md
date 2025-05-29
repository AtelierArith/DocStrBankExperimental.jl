```
change_representer(M::GeneralizedGrassmann, ::EuclideanMetric, p, X)
```

`X`を、スケーリングされたメトリックに関する点`p`でのコタンジェントベクトルの対応する表現者に変更します。すなわち、

$$
g_p(X,Y) = \operatorname{tr}(Y^{\mathrm{H}}BZ) = \operatorname{tr}(X^{\mathrm{H}}Z) = ⟨X,Z⟩
$$

がすべての$Z$に対して成り立つ必要があり、表現者`X`が与えられた場合、[`GeneralizedGrassmann`](@ref)上のメトリックに関する結果の表現者は$Y = B^{-1}X$で与えられます。
