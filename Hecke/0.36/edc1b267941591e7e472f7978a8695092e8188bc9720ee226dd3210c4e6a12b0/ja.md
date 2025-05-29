```
submodules(T::TorQuadModule; kw...)
```

`T`の部分モジュールをイテレータとして返します。部分モジュールを制限するための可能なキーワード引数：

  * `order::Int`: 順序が`order`の部分モジュールのみ、
  * `index::Int`: 指数が`index`の部分モジュールのみ、
  * `subtype::Vector{Int}`: アーベル群として`abelian_group(subtype)`と同型の部分モジュールのみ、
  * `quotype::Vector{Int}`: 商がアーベル群として`abelian_group(quotype)`と同型の部分モジュールのみ。
