```
broadcast_dims!(f, dest::AbstractDimArray, sources::AbstractDimArray...) => dest
```

ブロードキャスト関数 `f` を `sources` の `AbstractDimArray` に対して実行し、`dest` に書き込みます。 `sources` は、必要に応じて次元を並べ替えたり形を変えたりします。

結果には、渡されたすべての配列のすべての次元が含まれ、見つかった順序で表示されます。

## 引数

  * `dest`: 更新する `AbstractDimArray`。
  * `sources`: `f` でブロードキャストする `AbstractDimArrays`。
