```
copy_constructor(typename, fields::Vector{TypedVar}; [input_var::Symbol], [lnn::Union{LineNumberNode, Nothing}], [whereparams=not_provided], [copy_expr=default_copy_expr])
```

`typename` と `fields` のための `FuncDef` コピーコンストラクタを返します。すなわち、次の形式の関数です。

```julia
    $typename($input_var::$typename; field1::fieldtype1=Base.copy(getfield($input_var, :field1)), ...) = $typename(field1, ...)
```

オプションで提供される `lnn` と `whereparams` をサポートします。

`copy_expr(name, input_value)` は、フィールド `name` が `input_value` からどのようにコピーされるかを決定する `Expr` を返さなければなりません。
