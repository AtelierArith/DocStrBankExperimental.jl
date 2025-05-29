```
DetEqModel(tree::AbstractTree,
    probabilities,
    sub_problem_builder::Function,
    solver
    discount_factor=1.0,
    risk=RiskNeutral,
    sideconstraints=nothing,
    check=true,
    perfect_foresight = false
)
```

確率的容量拡張問題の決定論的同等モデルを定義します。

### 必要な引数

`tree` はシナリオツリーへの参照です。

`probabilities` は、ツリー内のすべてのノードの確率の辞書を返す関数、または単にその辞書自体です。

`sub_problem_builder` は、各サブ問題のためのJuMPモデルにノードをマッピングする関数です。

`solver` は、この問題に使用される最適化器への参照です（適切な設定を持つ）。

### オプションの引数

`discount_factor` は、シナリオツリー内の各アークに沿った定数割引率を定義する0から1の間の数値です。

`risk` は、2つのCVaRパラメータを持つタプルです: (λ, α)

`sideconstraints` は、マスタープロブレムにおけるサイド制約を指定する関数です。詳細については、[Tutorial 9: Side-constraints](@ref)を参照してください。

`check` はブール値で、JuDGEモデルの検証を無効にするために`false`に設定できます。

### 例

```
deteq = DetEqModel(tree, ConditionallyUniformProbabilities, sub_problems,
                                Gurobi.Optimizer)
judge = DetEqModel(tree, probabilities, sub_problems, CPLEX.Optimizer,
                                discount_factor=0.9, risk=(0.5,0.1)))
```
