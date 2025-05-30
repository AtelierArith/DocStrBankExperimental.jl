```
SafeRules{A, L, U} <: EliminationAlgorithm

SafeRules(alg::EliminationAlgorithm, lb::WidthOrAlgorithm, ub::EliminationAlgororithm)

SafeRules()
```

グラフを安全な削減ルールを使用して前処理します。アルゴリズム `lb` は木幅の下限を計算するために使用されます。より良い下限は、アルゴリズムがより多くの削減を行うことを可能にします。

```julia-repl
julia> using CliqueTrees, TreeWidthSolver

julia> graph = [
           0 1 0 0 0 0 0 0
           1 0 1 0 0 1 0 0
           0 1 0 1 0 1 1 1
           0 0 1 0 0 0 0 0
           0 0 0 0 0 1 1 0
           0 1 1 0 1 0 0 0
           0 0 1 0 1 0 0 1
           0 0 1 0 0 0 1 0
       ];

julia> alg1 = BT()
BT

julia> alg2 = SafeRules(BT(), MMW(), MF())
SafeRules{BT, MMW, MF}:
    BT
    MMW
    MF

julia> @time treewidth(graph; alg=alg1) # 遅い
  0.000177 秒 (1.41 k アロケーション: 90.031 KiB)
2

julia> @time treewidth(graph; alg=alg2) # 速い
  0.000044 秒 (282 アロケーション: 15.969 KiB)
2
```

### パラメータ

  * `alg`: 除去アルゴリズム
  * `lb`: 下限アルゴリズム（木幅の下限を求めるために使用）
  * `ub`: 除去アルゴリズム（木幅の上限を求めるために使用）

### 参考文献

  * Bodlaender, Hans L., et al. "確率的ネットワークの三角化のための前処理." (2001).
  * Bodlaender, Hans L., Arie M.C.A. Koster, and Frank van den Eijkhof. "確率的ネットワークの三角化のための前処理ルール." *Computational Intelligence* 21.3 (2005): 286-305.
  * van den Eijkhof, Frank, Hans L. Bodlaender, and Arie M.C.A. Koster. "重み付き木幅のための安全な削減ルール." *Algorithmica* 47 (2007): 139-158.
