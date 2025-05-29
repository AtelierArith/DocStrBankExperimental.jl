```
bellman(V, prob; upper_bound = false)
```

ロバストベルマン更新を、価値関数 `V` と、価値関数 `V` の期待値の上限または下限をO-最大化によって制約する区間確率 `prob` を用いて計算します[1]。期待値が最大化されるか最小化されるかは、`upper_bound` キーワード引数によって決まります。つまり、`upper_bound == true` の場合は上限が計算され、`upper_bound == false` の場合は下限が計算されます。

### 例

```jldoctest
prob = IntervalProbabilities(;
    lower = sparse_hcat(
        SparseVector(15, [4, 10], [0.1, 0.2]),
        SparseVector(15, [5, 6, 7], [0.5, 0.3, 0.1]),
    ),
    upper = sparse_hcat(
        SparseVector(15, [1, 4, 10], [0.5, 0.6, 0.7]),
        SparseVector(15, [5, 6, 7], [0.7, 0.5, 0.3]),
    ),
)

Vprev = collect(1:15)
Vcur = bellman(Vprev, prob; upper_bound = false)
```

!!! note
    この関数はワークスペースオブジェクトと出力ベクトルを構築します。ホットループの場合、`bellman!` を使用して事前に割り当てられたオブジェクトを渡す方が効率的です。


[1] M. Lahijanian, S. B. Andersson and C. Belta, "Formal Verification and Synthesis for Discrete-Time Stochastic Systems," in IEEE Transactions on Automatic Control, vol. 60, no. 8, pp. 2031-2045, Aug. 2015, doi: 10.1109/TAC.2015.2398883.
