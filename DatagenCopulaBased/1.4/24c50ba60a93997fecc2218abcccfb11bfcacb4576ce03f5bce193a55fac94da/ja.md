```
階層的ガンベルコピュラ
```

フィールド:

  * n::Int - マージナルの数
  * θ::Vector{Real} - パラメータのベクトル、減少している必要があり、θ[end] ≧ 1でなければならない

十分なネスティング条件が満たされるために。

階層的にネストされたガンベルコピュラ C*θₙ₋₁(C*θₙ₋₂( ... C*θ₂(C*θ₁(u₁, u₂), u₃)...uₙ₋₁) uₙ)

コンストラクタ

```
HierarchicalGumbelCopula(θ::Vector{Real})
```

コンストラクタ

```
HierarchicalGumbelCopula(ρ::Vector{Real}, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するには、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の場所に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest

julia> c = HierarchicalGumbelCopula([5., 4., 3.])
HierarchicalGumbelCopula(4, [5.0, 4.0, 3.0])

julia> c = HierarchicalGumbelCopula([0.95, 0.5, 0.05], KendallCorrelation)
HierarchicalGumbelCopula(4, [19.999999999999982, 2.0, 1.0526315789473684])
```
