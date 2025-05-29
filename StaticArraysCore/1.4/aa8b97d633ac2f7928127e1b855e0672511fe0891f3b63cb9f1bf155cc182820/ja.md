```
abstract FieldArray{N, T, D} <: StaticArray{N, T, D}
```

この型を継承することで、自分自身のランク-D テンソル型を簡単に作成できます。`FieldArray` は自動的に `getindex` と `setindex!` を適切に定義します。不変の `FieldArray` は、同様の長さと要素型の `SArray` と同じくらいの性能を持ち、可変の `FieldArray` は `MArray` と似たように振る舞います。

任意の `FieldArray` サブタイプのフィールドは、列優先順序で定義する必要があることに注意してください。代替の順序を使用したい場合は、`getindex`、`setindex!`、およびタプル変換の独自の定義を提供する際に特別な注意を払う必要があります。

要素型に対してパラメトリックな `FieldArray` を定義する場合は、`FieldVector` の例のように `similar_type` を定義することを検討してください。

# 例

```
struct Stiffness <: FieldArray{Tuple{2,2,2,2}, Float64, 4}
    xxxx::Float64
    yxxx::Float64
    xyxx::Float64
    yyxx::Float64
    xxyx::Float64
    yxyx::Float64
    xyyx::Float64
    yyyx::Float64
    xxxy::Float64
    yxxy::Float64
    xyxy::Float64
    yyxy::Float64
    xxyy::Float64
    yxyy::Float64
    xyyy::Float64
    yyyy::Float64
end
```
