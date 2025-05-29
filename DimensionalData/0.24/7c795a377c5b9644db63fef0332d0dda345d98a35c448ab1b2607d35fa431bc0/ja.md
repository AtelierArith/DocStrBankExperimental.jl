```
units(x) => Union{Nothing,Any}
units(xs:Tuple) => Tuple
unit(A::AbstractDimArray, dims::Tuple) => Tuple
unit(A::AbstractDimArray, dim) => Union{Nothing,Any}
```

配列または `Dimension`、またはそれらのタプルの単位を取得します。

単位には設定されたフィールドがなく、`metadata` に含まれている場合と含まれていない場合があります。このメソッドは、単位が利用可能な場合にラベルやプロットでの使用を容易にするためのものであり、単位が必ず存在することを保証するものではありません。利用できない場合は、`nothing` が返されます。

第二引数 `dims` は、`Dimension`、`Dimension` 型、または `Dim{Symbol}` のための `Symbols` である可能性があります。
