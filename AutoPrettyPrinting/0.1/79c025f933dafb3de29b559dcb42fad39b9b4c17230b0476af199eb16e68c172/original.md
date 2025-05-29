```
@decorators [separators=nothing] [parentheses=nothing] expr
```

Executes `expr` using the prescribed decorator strings specified in `kwargs`.

If provided, `separators` must be of the form `(key1=value1, ...)` and the provided values must resolve to a `String` type If provided, `parentheses` must be of the form `(key1=value1, ...)` and the provided values must resolve to a `Tuple{String, String}` type

# Arguments

## Separators

  * `horiz` - separator string used when joining items horizontally
  * `kv` - separator string used when rendering `KeyValue` pairs
  * `pair` - separator string used when rendering `Pair` objects

## Parentheses

  * `vector` - start + end parentheses used when rendering `AbstractVector`s
  * `set` - start + end parentheses used when rendering `AbstractSet`s
  * `dict` - start + end parentheses used when rendering `AbstractDict` and `AbstractDictionary`s
  * `tuple` - start + end parentheses used when rendering `Tuple`s
  * `named_tuple` - start + end parentheses used when rendering `NamedTuple`s
