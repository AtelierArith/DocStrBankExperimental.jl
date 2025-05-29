```
broadcast_dims(f, sources::AbstractDimArray...) => AbstractDimArray
```

関数 `f` を `sources` の `AbstractDimArray` に対してブロードキャストし、必要に応じて次元を並べ替えたり形を変えたりします。結果には、渡されたすべての配列のすべての次元が、見つかった順序で含まれます。

## 引数

  * `sources`: `f` でブロードキャストする `AbstractDimArrays`。

これは、`A` のすべてのスライスに対して、`B` の次元でスライスされている場合にブロードキャストするのと似ています。
