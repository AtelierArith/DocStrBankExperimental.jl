```
TemplateExpression{T,F,N,E,TS,D} <: AbstractExpression{T,N}
```

複数のサブエクスプレッションを構造的に組み合わせることを可能にする象徴的な表現であり、変数の使用に関する制約があります。

`TemplateExpression` は、ドメイン固有の知識や制約をモデルの構造に課す必要がある象徴的回帰タスクのために設計されています。

# コンストラクタ

  * `TemplateExpression(trees; structure, operators, variable_names)`

      * `trees`: サブエクスプレッションを保持する `NamedTuple`（例: `f = Expression(...)`, `g = Expression(...)`）。
      * `structure`: サブエクスプレッションが異なるコンテキストでどのように組み合わされるかを定義する関数を保持する `TemplateStructure`。
      * `operators`: サブエクスプレッションに対して許可される演算子を定義する `OperatorEnum`。
      * `variable_names`: データセット内の変数の名前を定義するオプションの `String` の `Vector`。

# 例

2つのサブエクスプレッション `f(x1, x2)` と `g(x3)` を組み合わせた `TemplateExpression` の例を作成してみましょう：

```julia
# 演算子と変数名を定義
options = Options(; binary_operators=(+, *, /, -), unary_operators=(sin, cos))
operators = options.operators
variable_names = ["x1", "x2", "x3"]

# サブエクスプレッションを作成
x1 = Expression(Node{Float64}(; feature=1); operators, variable_names)
x2 = Expression(Node{Float64}(; feature=2); operators, variable_names)
x3 = Expression(Node{Float64}(; feature=3); operators, variable_names)

# TemplateExpressionを作成
example_expr = (; f=x1, g=x3)
st_expr = TemplateExpression(
    example_expr;
    structure=TemplateStructure{(:f, :g)}(
        ((; f, g), (x1, x2, x3)) -> sin(f(x1, x2)) + g(x3)^2
    ),
    operators,
    variable_names,
)
```

SymbolicRegression.jlでモデルをフィッティングする際には、`expression_spec=TemplateExpressionSpec(; structure=TemplateStructure(...))` をオプションとして提供できます。`variable_constraints` は `f` が `x1` と `x2` のみにアクセスできるように制約し、`g` が `x3` のみにアクセスできるように制約します。
