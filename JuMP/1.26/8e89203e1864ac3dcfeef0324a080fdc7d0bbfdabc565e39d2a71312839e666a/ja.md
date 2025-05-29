```
show_objective_function_summary(io::IO, model::AbstractModel)
```

`io`に目的関数のタイプの要約を書き込みます。

## 拡張

`AbstractModel`はこのメソッドを実装する必要があります。

## 例

```jldoctest
julia> model = Model();

julia> show_objective_function_summary(stdout, model)
目的関数のタイプ: AffExpr
```
