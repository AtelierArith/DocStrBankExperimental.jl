```
StorageScalar = Union{StorageReal, <:AbstractString}
```

スカラーとして使用できる型、または格納された行列やベクトルの要素。

これは[`StorageReal`](@ref)（ブール値を含む）および文字列に制限されています。原則として任意の`isbitstype`をサポートできるため、あまりにも制限が厳しいと言えるでしょう。しかし、実際には他のシステム（特にPythonやR）からデータにアクセスする際に多くの問題を引き起こすことになります。`Daf`は「何でも」ではなく、科学データ（特に生物学的データ）を格納することを目的としているため、この制限は合理的に思えます。
