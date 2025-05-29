```
stable_submodules(T::TorQuadModule, act::Vector{TorQuadModuleMap}; kw...)
```

`act`の自己準同型に対して安定な`T`の部分モジュールをイテレータとして返します。部分モジュールを制限するための可能なキーワード引数：

  * `quotype::Vector{Int}`: 商が`abelian_group(quotype)`としてアーベル群に同型である部分モジュールのみ。
