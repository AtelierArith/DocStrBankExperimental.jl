```
fcreate(N::Union{Int,Val}, j::Int)
```

`j`-番目のサイトに作用するフェルミオン生成演算子を構築します。ファック空間は合計で`N`サイトを持ちます：

ここでは、[ジョルダン・ウィグナー変換](https://en.wikipedia.org/wiki/Jordan%E2%80%93Wigner_transformation)を使用します。すなわち、

$$
\hat{d}^\dagger_j = \hat{\sigma}_z^{\otimes j-1} \otimes \hat{\sigma}_{-} \otimes \hat{\mathbb{1}}^{\otimes N-j}
$$

サイトインデックス`j`は次の条件を満たす必要があります：`1 ≤ j ≤ N`。

ここでは、$|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$を基底（空）状態、$|1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$を励起（占有）状態と考えるため、$\hat{\sigma}_{-} = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}$としています。

!!! warning "型の安定性に注意！"
    型の安定性を保ちたい場合は、`fcreate(Val(N), j)`を使用することをお勧めします。`fcreate(N, j)`の代わりに。型の安定性に関する詳細は、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)および[関連セクション](@ref doc:Type-Stability)を参照してください。

