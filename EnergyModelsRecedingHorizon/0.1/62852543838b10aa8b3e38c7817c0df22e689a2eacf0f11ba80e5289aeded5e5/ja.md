```
struct TypeFutureValue <: FutureValue
TypeFutureValue(element_type::Type{<:AbstractElement}, key::Symbol, val::Real)
```

特定のノードタイプとモデルキーに対する将来価値。これは最終的な値のみを利用し、指定されたタイプのすべてのインスタンスにコスト関数に直接追加します。

## フィールド

  * **`element::Type{<:AbstractElement}`** は、将来価値が適用されるノードタイプです。
  * **`val_dict::Dict{Symbol, Real}`** は、将来価値を計算するために与えられた値でキーとして提供される変数を含む辞書です。値の単位を考慮することが重要です。

!!! info "単一変数"
    フィールド `val_dict` は、単一の変数のみを制限する必要がある場合、キーと値の入力としても提供できます。


!!! danger "TypeFutureValueの適用"
    `TypeFutureValue` は、特定のタイプのすべてのインスタンスに将来価値を割り当てます。参照ノードには**決して**使用してはいけません。他のノードタイプの動的変数にのみ使用する必要があります。

