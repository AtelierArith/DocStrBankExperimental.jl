```
rebuild(x; kw...)
```

フィールド値が更新されたオブジェクト構造を再構築します。

`x` は `AbstractDimArray`、`Dimension`、`Lookup` またはその他のカスタムタイプであることができます。

これは、DimensionalData.jl のほとんどのオブジェクトが不変であるため、組み込みおよびカスタムタイプを再構築してフィールドを更新できるようにする抽象化です。

再構築は主に `ConstructionBase.setproperties` を使用して自動化されています。オブジェクトが DimensionalData オブジェクトとは異なる名前のフィールドを持つ場合にのみ定義する必要があります。そうしないようにしてください！

必要な引数は、`rebuild` メソッドを持つ抽象型に対して定義されています。

#### `AbstractBasicDimArray`:

  * `dims`: `Dimension` の `Tuple`

#### `AbstractDimArray`:

  * `data`: 親オブジェクト - `AbstractArray`
  * `dims`: `Dimension` の `Tuple`
  * `refdims`: `Dimension` の `Tuple`
  * `name`: シンボル、または GPU 上の `NoName` と `Name`
  * `metadata`: `Dict` のようなオブジェクト

#### `AbstractDimStack`:

  * `data`: 親オブジェクト、しばしば `NamedTuple`
  * `dims`、`refdims`、`metadata`

#### `Dimension`:

  * `val`: 何でも。

#### `Lookup`:

  * `data`: 親オブジェクト、`AbstractArray`
  * 注: 引数 `rebuild` は `AbstractDimArray` および `AbstractDimStack` で非推奨となり、常にキーワードバージョンを使用することが推奨されます。将来的には、引数バージョンは `Dimension` のみに使用され、これは1つの引数しか持ちません。
