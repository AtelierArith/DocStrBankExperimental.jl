```
alphabet(
    X::PropositionalLogiset,
    sorted=true;
    test_operators::Union{Nothing,AbstractVector{<:TestOperator},Base.Callable}=nothing,
    discretizedomain=false,
    y::Union{Nothing, AbstractVector}=nothing,
)::MultivariateScalarAlphabet
```

提供された `PropositionalLogiset` `X` に基づいてアルファベットを構築します。オプションのパラメータは次のとおりです：

  * `sorted`: サブアルファベット（すなわち、閾値ドメイン）内の原子を、真先に来るポリシーでソートするかどうか（デフォルト: true）
  * `test_operators`: 使用するテストオペレーター（実値特徴の場合は `[≤, ≥]`、他の特徴（例：カテゴリカル）の場合は `[(==), (≠)]` にデフォルト設定）
  * `discretizedomain`: ドメインを離散化するかどうか（デフォルト: false）
  * `y`: 離散化に使用されるベクトル（`discretizedomain` が true の場合は必須）

`ScalarCondition` と `UnivariateScalarAlphabet` を含む `UnionAlphabet` を返します。
