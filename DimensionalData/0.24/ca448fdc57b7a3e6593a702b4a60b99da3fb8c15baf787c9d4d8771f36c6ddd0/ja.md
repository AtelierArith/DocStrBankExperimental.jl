```
AbstractDimArray <: AbstractArray
```

すべての「dim」配列のための抽象スーパタイプです。

これらの配列は、[`dims`](@ref) メソッドから [`Dimension`](@ref) の `Tuple` を返し、[`rebuild`](@ref) を使用して再構築できます。

`parent` はソース配列を返さなければなりません。

これらは [`metadata`](@ref)、[`name`](@ref)、および [`refdims`](@ref) メソッドを持つべきですが、これらはオプションです。

`AbstractDimArray` のための [`rebuild`](@ref) メソッドは、`data`、`dims`、`refdims`、`name`、`metadata` 引数を受け入れなければなりません。

非範囲の `AbstractArray` で `AbstractDimArray` をインデックス付けすることは、`Dimension` インデックスに未定義の影響を与えます。前方順序の配列のみを使用してください。
