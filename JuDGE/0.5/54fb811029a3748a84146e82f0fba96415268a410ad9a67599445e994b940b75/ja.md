```
JuDGEModel(tree::AbstractTree,
           probabilities,
           sub_problem_builder::Function,
           solver;
           discount_factor=1.0,
           risk=RiskNeutral(),
           sideconstraints=nothing,
           check=true,
           perfect_foresight=false)
```

JuDGEモデルを定義します。

### 必要な引数

`tree` はシナリオツリーへの参照です。

`probabilities` は、ツリー内のすべてのノードの確率の辞書を返す関数、または単にその辞書自体です。

`sub_problem_builder` は、各サブプロブレムのためのJuMPモデルにノードをマッピングする関数です。

`solver` はマスタープロブレムに使用される最適化器への参照です（適切な設定を持つ）。これは、緩和を解くための最適化器と、バイナリモデルを解くための最適化器の2つのタプルであることもできます。

### オプションの引数

`discount_factor` は、シナリオツリー内の各アークに沿った定数割引率を定義する0から1の間の数値です。

`risk` は `Risk` オブジェクト、またはそのようなオブジェクトのベクトルである可能性があります。

`sideconstraints` は、マスタープロブレムにおけるサイド制約を指定する関数です。詳細については、[Tutorial 9: Side-constraints](@ref)を参照してください。

`check` はブール値で、JuDGEモデルの検証を無効にするために `false` に設定できます。

`perfect_foresight` はブール値で、これは実験的な機能であり、各リーフノードのために1つのJuDGEモデルの配列を作成します。これにより、ユーザーは確率プログラムのEVPIを簡単に計算できます。また、後悔ベースのリスク実装にも使用できます。例としては、EVPI*and*VSS.jlを参照してください。

### 例

```
judge = JuDGEModel(tree, ConditionallyUniformProbabilities, sub_problems,
                                Gurobi.Optimizer)
judge = JuDGEModel(tree, probabilities, sub_problems, CPLEX.Optimizer,
                                discount_factor=0.9, risk=Risk(0.5,0.1)))
```
