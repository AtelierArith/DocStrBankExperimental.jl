```
mangalnetwork(MN::Mangal.MangalNetwork, query::Pair...; taxonlevel::Bool=false)
```

[mangal.io](https://mangal.io) からネットワークを取得します。`Mangal.jl` API ラッパーを使用します。キーワード引数 `taxonlevel` は、元の *node* またはその *reference taxon* を使用する必要があるかどうかを指定します。すべてのノードに明確に関連付けられたリファレンスタクソンがあるわけではないことに注意してください。

ネットワークは *常に* 定量的な単一部ネットワークとして返されます。これは情報の損失が *ない* 形式だからです。異なる表現に変換したい場合は、[`render`](@ref) メソッドを使用できます。

最初の引数として ID またはネットワーク名を使用することもできます。より複雑なクエリを行いたい場合は、次のように `Mangal` パッケージをインポートできます。

```
using SpeciesInteractionNetworks
import SpeciesInteractionNetworks.Mangal
```

###### 参考文献

[Poisot2016mangal](@citet*)
