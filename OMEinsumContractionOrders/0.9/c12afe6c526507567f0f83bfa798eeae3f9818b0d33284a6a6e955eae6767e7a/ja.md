```
struct Treewidth{EL <: EliminationAlgorithm, GM} <: CodeOptimizer
Treewidth(; alg::EL = SafeRules(BT(), MMW{3}(), MF()), greedy_config::GM = GreedyMethod(nrepeat=1))
```

木幅に基づくソルバー。ソルバーは [CliqueTrees.jl](https://algebraicjulia.github.io/CliqueTrees.jl/stable/) と [TreeWidthSolver.jl](https://github.com/ArrogantGao/TreeWidthSolver.jl) に実装されています。これらには以下が含まれます：

| アルゴリズム   | 説明                   | 時間計算量    | 空間計算量    |
|:-------- |:-------------------- |:-------- |:-------- |
| `BFS`    | 幅優先探索                | O(m + n) | O(n)     |
| `MCS`    | 最大基数探索               | O(m + n) | O(n)     |
| `LexBFS` | 辞書順幅優先探索             | O(m + n) | O(m + n) |
| `RCMMD`  | 逆カサリル・マッキー（最小次数）     | O(m + n) | O(m + n) |
| `RCMGL`  | 逆カサリル・マッキー（ジョージ・リュー） | O(m + n) | O(m + n) |
| `MCSM`   | 最大基数探索（最小）           | O(mn)    | O(n)     |
| `LexM`   | 辞書順幅優先探索（最小）         | O(mn)    | O(n)     |
| `AMF`    | 近似最小充填               | O(mn)    | O(m + n) |
| `MF`     | 最小充填                 | O(mn²)   | -        |
| `MMD`    | 複数最小次数               | O(mn²)   | O(m + n) |

詳細な説明は [CliqueTrees.jl](https://algebraicjulia.github.io/CliqueTrees.jl/stable/api/#Elimination-Algorithms) で入手できます。

# フィールド

  * `alg::EL`: 木幅計算に使用するアルゴリズム。利用可能な消去アルゴリズムは上記にリストされています。
  * `greedy_config::GM`: 貪欲法の設定。

# 例

```jldoctest
julia> optimizer = Treewidth();

julia> eincode = OMEinsumContractionOrders.EinCode([['a', 'b'], ['a', 'c', 'd'], ['b', 'c', 'e', 'f'], ['e'], ['d', 'f']], ['a'])
ab, acd, bcef, e, df -> a

julia> size_dict = Dict([c=>(1<<i) for (i,c) in enumerate(['a', 'b', 'c', 'd', 'e', 'f'])]...)
Dict{Char, Int64} with 6 entries:
  'f' => 64
  'a' => 2
  'c' => 8
  'd' => 16
  'e' => 32
  'b' => 4

julia> optcode = optimize_code(eincode, size_dict, optimizer)
ab, ab -> a
├─ fac, bcf -> ab
│  ├─ df, acd -> fac
│  │  ├─ df
│  │  └─ acd
│  └─ e, bcef -> bcf
│     ├─ e
│     └─ bcef
└─ ab
```
