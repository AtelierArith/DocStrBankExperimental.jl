```
put!(algo::AbstractImageReconstructionAlgorithm, inputs...)
```

与えられた `inputs` に対してアルゴリズム `algo` を使用して画像再構成を行います。アルゴリズムによっては、これがブロックされる場合があります。結果は保存され、`take!` を使用して取得できます。
