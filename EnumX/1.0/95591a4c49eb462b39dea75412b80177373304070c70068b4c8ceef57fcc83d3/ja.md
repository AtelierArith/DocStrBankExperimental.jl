```
@enumx
```

インスタンスを持つ列挙型を生成するためのマクロ。

`@enumx` は `Base` の `@enum` の代替として使用でき、いくつかの改善があります。詳細については、[README](https://github.com/fredrikekre/EnumX.jl) またはモジュールのドキュメント文字列（REPL での `?EnumX`）を参照してください。

# 例

```julia
julia> @enumx Fruit Apple Banana

julia> Fruit.T
Enum type Fruit.T <: Enum{Int32} with 2 instances:
 Fruit.Apple  = 0
 Fruit.Banana = 1

julia> Fruit.Apple
Fruit.Apple = 0
```
