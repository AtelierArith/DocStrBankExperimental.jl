```julia
struct BlobEntry
```

`BlobEntry`は、実際のblobを見つけるための参照情報を保持する構造化データの小さな単位です。多くの`BlobEntry`が、エージェントやファクターグラフにまたがる異なるグラフノード上に存在し、すべて同じ`Blob`を参照することができます。

注意:

  * `blobId`はblobstore内で一意であり、不変です。
