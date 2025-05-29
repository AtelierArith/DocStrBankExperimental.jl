```
get_contents(ex::AbstractExpression)
```

式の内容を取得します。これは、単純な `AbstractExpressionNode` であるか、それらの組み合わせ、または他のデータである可能性があります。これは、[`get_metadata`](@ref) によって返されるもの以外のすべてを含むべきです。
