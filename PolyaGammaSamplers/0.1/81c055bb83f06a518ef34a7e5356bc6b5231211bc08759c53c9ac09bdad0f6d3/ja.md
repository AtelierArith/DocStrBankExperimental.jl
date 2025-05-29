```
PolyaGammaPSWSampler(b::Int, z::Real)
```

PSWサンプラー ([1]) は、パラメータ `b` と `z` を持つポリヤ-ガンマ分布のためのもので、ラプラス変換は次のようになります。

$$
\mathcal{L}(t) = \cosh^b(z) \cosh^{-b}(\sqrt{2t + z^2})
$$

参考文献

  * [1] [https://doi.org/10.1080/01621459.2013.829001](https://doi.org/10.1080/01621459.2013.829001)
