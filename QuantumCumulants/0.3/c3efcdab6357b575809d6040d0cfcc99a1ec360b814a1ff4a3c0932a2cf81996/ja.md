```
MeanfieldEquations <: AbstractMeanfieldEquations
```

微分方程のシステムを定義する型であり、`lhs`は導関数のベクトル、`rhs`は表現のベクトルです。さらに、ハミルトニアン、崩壊演算子、およびシステムの対応する減衰率を追跡します。

# フィールド

*`equations`: 平均の微分方程式のベクトル。 *`operator_equations`: 演算子の微分方程式のベクトル。 *`states`: 方程式の左辺にある平均を含むベクトル。 *`operators`: 方程式の左辺にある演算子を含むベクトル。 *`hamiltonian`: システムのハミルトニアンを定義する演算子。 *`jumps`: 減衰プロセスを指定する演算子のベクトル。 *`jumps`: 減衰プロセスの随伴を指定する演算子のベクトル。 *`rates`: `jumps`に対応する減衰率。 *`iv`: システムの独立変数（時間パラメータ）。 *`varmap`: 平均を時間依存変数にマッピングするペアのベクトル。 この形式はModelingToolkitの機能に必要です。 *`order`: [`cumulant_expansion`](@ref)が実行された順序。
