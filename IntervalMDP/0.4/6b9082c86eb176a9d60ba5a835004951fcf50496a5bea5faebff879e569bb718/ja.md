```
IntervalProbabilities{R, VR <: AbstractVector{R}, MR <: AbstractMatrix{R}}
```

すべてのソース状態またはソース/アクションペアからすべてのターゲット状態への下限および上限遷移確率を表す行列ペア。行列は `Matrix{R}` または `SparseMatrixCSC{R}`、またはそのCUDAの同等物であることができます。メモリ効率のために、疎行列を使用することをお勧めします。

列はソースを表し、行はターゲットを表します。確率行列が線形変換であるかのように。数学的に、$P$ を確率行列とします。すると、$P_{ij}$ は状態 $j$（または状態/アクションペア $j$）から状態 $i$ への遷移確率を表します。Juliaの列優先形式のため、これはキャッシュの局所性の観点からもより効率的な表現です。

下限は明示的に保存され、上限は下限とギャップから計算されます。この選択は、O-最大化を使用した繰り返しの確率割り当てを簡素化するためです [1]。

### フィールド

  * `lower::MR`: ソース状態またはソース/アクションペアからターゲット状態への下限遷移確率。
  * `gap::MR`: ソース状態またはソース/アクションペアからターゲット状態への上限と下限遷移確率のギャップ。
  * `sum_lower::VR`: ソース状態またはソース/アクションペアからすべてのターゲット状態への下限遷移確率の合計。

### 例

```jldoctest
dense_prob = IntervalProbabilities(;
    lower = [0.0 0.5; 0.1 0.3; 0.2 0.1],
    upper = [0.5 0.7; 0.6 0.5; 0.7 0.3],
)

sparse_prob = IntervalProbabilities(;
    lower = sparse_hcat(
        SparseVector(15, [4, 10], [0.1, 0.2]),
        SparseVector(15, [5, 6, 7], [0.5, 0.3, 0.1]),
    ),
    upper = sparse_hcat(
        SparseVector(15, [1, 4, 10], [0.5, 0.6, 0.7]),
        SparseVector(15, [5, 6, 7], [0.7, 0.5, 0.3]),
    ),
)
```

[1] M. Lahijanian, S. B. Andersson and C. Belta, "Formal Verification and Synthesis for Discrete-Time Stochastic Systems," in IEEE Transactions on Automatic Control, vol. 60, no. 8, pp. 2031-2045, Aug. 2015, doi: 10.1109/TAC.2015.2398883.
