```
get_metadata(ex::AbstractExpression)
```

式のメタデータを取得します。これは、単純な `NamedTuple` であるか、それらの組み合わせ、または他のデータである可能性があります。これには、[`get_contents`](@ref) によって返されるもの以外のすべてが含まれるべきです。
