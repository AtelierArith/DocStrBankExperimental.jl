このマクロは [`@frompackage`](@ref) と同等ですが、呼び出しファイルを `target` 引数として仮定します。したがって、次のコード 

```
@fromparent import_block
```

は次のように等価です。

```
@frompackage @__FILE__ import_block
```

その使用法を理解するために、[`@frompackage`](@ref) のドキュメントとパッケージ [ドキュメント](https://disberd.github.io/PlutoDevMacros.jl/dev/frompackage/introduction/#Introduction) を参照してください。また、[`@addmethod`](@ref) もご覧ください。
