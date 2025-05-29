すべての還元操作のための抽象型。

文字列クエリでは、これは `%>` 演算子を使用して指定されます（例：`%> Sum`、`%> Quantile fraction 0.05`）：

`ReductionOperation` := `%>` 演算 ( パラメータ値 )*

各 `ReductionOperation` は [`QueryOperation`](@ref) であるため、クエリに直接適用できます（例：`Axis("cell") |> Axis("gene") |> Lookup("UMIs") |> Quantile(0.05)`）。このためには、この使用法に合わせた他のコンストラクタが必要です。

還元操作は行列またはベクトルデータに適用できます。データの1次元を削減（排除）し、結果は入力とは異なるデータ型になる可能性があります。ベクトルに適用されると、操作はスカラーを返します。行列に適用されると、行列は列優先レイアウトであると仮定し、各列をスカラーに削減した結果を含むベクトルを返します。

新しい操作を実装するには、型は次の形式である必要があります：

```
struct MyOperation <: ReductionOperation
    ... オプションのパラメータ ...
end

MyOperation(operation_name::Token, parameter_values::Dict{String, Token})::MyOperation
```

コンストラクタは、各パラメータに対して `parse_parameter` を使用する必要があります（例えば、通常 `parse_number_assignment` を使用）。さらに、クエリで使用できるように操作を登録するために [`@query_operation`](@ref) を呼び出し、以下に示す関数を実装する必要があります。詳細と例については、クエリ操作モジュールを参照してください。
