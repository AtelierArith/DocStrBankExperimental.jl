すべての要素ごとの操作のための抽象型。

文字列クエリでは、`%` 演算子を使用して指定されます（例：`% Abs`、`% Log base 2`）：

`EltwiseOperation` := `%` 演算（パラメータ値）*

各 `EltwiseOperation` は [`QueryOperation`](@ref) であるため、クエリに直接適用できます（例：`Axis("cell") |> Lookup("age") |> Abs()`）。この用途に合わせた他のコンストラクタが必要です。

要素ごとの操作は、スカラー、ベクトル、または行列データに適用できます。データの形状は保持されますが、値が変更され、要素のデータ型が変更される可能性があります。たとえば、`Abs` は各値の絶対値を計算します。

新しい操作を実装するには、型は次の形式である必要があります：

```
struct MyOperation <: EltwiseOperation
    ... オプションのパラメータ ...
end
@query_operation MyOperation

MyOperation(operation_name::Token, parameter_values::Dict{String, Token})::MyOperation
```

コンストラクタは、各パラメータに対して `parse_parameter` を使用する必要があります（たとえば、`parse_number_assignment` を使用）。さらに、クエリで使用できるように操作を登録するために [`@query_operation`](@ref) を呼び出し、以下に示す関数を実装する必要があります。詳細と例については、クエリ操作モジュールを参照してください。
