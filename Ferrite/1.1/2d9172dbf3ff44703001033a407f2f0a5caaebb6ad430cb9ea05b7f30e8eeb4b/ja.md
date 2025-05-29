```
apply!(K::SparseMatrixCSC, rhs::AbstractVector, ch::ConstraintHandler)
```

行列 `K` と右辺 `rhs` を、`ch` で指定されたディリクレ境界条件を考慮するように調整し、`K \ rhs` が期待される解を与えるようにします。

!!! note
    `apply!(K, rhs, ch)` は本質的に次の計算を行います。

    ```julia
    rhs[free] = rhs[free] - K[constrained, constrained] * a[constrained]
    ```

    ここで、`a[constrained]` は不均一性です。したがって、`rhs` の符号が重要です（`apply_zero!` とは対照的に）。


```julia
apply!(v::AbstractVector, ch::ConstraintHandler)
```

解ベクトル `v` に、`ch` で指定されたディリクレ境界条件とアフィン制約を適用します。

# 例

```julia
K, f = assemble_system(...) # システムを組み立てる
apply!(K, f, ch)            # 境界条件を考慮して K と f を調整する
u = K \ f                   # システムを解く、u は「おおよそ正しい」べき
apply!(u, ch)               # 明示的に境界条件が正しいことを確認する
```

!!! note
    最後の操作は厳密には必要ありません。なぜなら、境界条件はすでに `apply!(K, f, ch)` の後に満たされているはずだからです。しかし、線形システムのソルバーは正確ではないため、`apply!(u, ch)` を使用して境界条件が正確に満たされていることを確認できます。

