```
BoundedAttributes(attrs; count_limit=nothing, value_length_limit=nothing)
```

これは、属性（通常は `AbstractDict` または `NamedTuple`）をラップして、[Attributeの仕様](https://opentelemetry.io/docs/reference/specification/common/#attribute)に従うものです。

`Base` からの以下のメソッドが `BoundedAttributes` に定義されており、デフォルトでは内部の `attrs` に転送されます。必要なメソッドが欠けている場合は、PRを作成してください：

  * `Base.getindex`
  * `Base.setindex!`
  * `Base.iterate`
  * `Base.length`
  * `Base.haskey`
  * `Base.push!`。明らかに、`NamedTuple` のような不変の `attrs` に対して呼び出すとエラーが発生します。
