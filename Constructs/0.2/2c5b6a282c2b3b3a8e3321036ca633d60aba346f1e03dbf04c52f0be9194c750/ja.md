```
Optional(T|subcon, [default = nothing]) -> Construct{Union{T, TV}}
Optional{TU}(T|subcon, [default = nothing]) -> Construct{TU}
```

デフォルト値を持つオプショナル構造。

# 引数

  * `TU`: 構造とデフォルト値の共通型。
  * `T<:TU`: サブ構造の型。
  * `TV<:TU`: デフォルト値の型。
  * `subcon::Construct{T}`: サブ構造。
  * `default::TV`: デフォルト値。
