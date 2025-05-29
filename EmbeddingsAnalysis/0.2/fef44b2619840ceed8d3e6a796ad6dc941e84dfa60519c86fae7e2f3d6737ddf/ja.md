```
similarity_order(wv::WordVectors, alpha=-0.65)
```

単語埋め込み `wv` を後処理し、モデルの類似性順序を調整する線形変換を通じて直接明らかである以上の情報をキャプチャするようにします。この関数は、処理された埋め込みを含む新しい `WordVectors` オブジェクトを返します。

# 引数

  * `wv::WordVectors` 単語埋め込み

# `alpha::AbstractFloat` アルゴリズムの `α` パラメータ (デフォルト -0.65)

# 参考文献:

  * [Artetxe et al. "Uncovering divergent linguistic information in  word embeddings with lessons for intrinsic and extrinsic evaluation",  2018](https://arxiv.org/pdf/1809.02094.pdf)
