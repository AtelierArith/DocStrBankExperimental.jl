```
@fill!(A, x)
@fill!(A, x)
```

`fill!(A, x)`を呼び出します。ここで、関数`fill`は、[`@init_parallel_stencil`](@ref)で選択された並列化用のパッケージと互換性があるように選択/実装されています。

# 引数

  * `A::Array|CellArray|TArray|TCellArray`: `x`で埋める配列。
  * `x::Number|Data.Index|Enum|Collection{Number|Data.Index|Enum, celldims}`: `A`を埋める内容。`A`がCellArrayの場合、`x`は単一の値または`A`のサイズ`celldims`の値のコレクション（例：配列、タプルなど）であることができます。

参照: [`@fill`](@ref)
