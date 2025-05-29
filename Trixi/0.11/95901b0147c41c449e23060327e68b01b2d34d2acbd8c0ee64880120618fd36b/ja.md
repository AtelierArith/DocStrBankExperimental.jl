```
initial_condition_poisson_nonperiodic(x, t, equations::HyperbolicDiffusionEquations1D)
```

非周期的な滑らかな初期条件。[`source_terms_poisson_nonperiodic`](@ref)および[`boundary_condition_poisson_nonperiodic`](@ref)と組み合わせて収束テストに使用できます。

!!! note
    解は周期的ですが、初期推定はそうではありません。

