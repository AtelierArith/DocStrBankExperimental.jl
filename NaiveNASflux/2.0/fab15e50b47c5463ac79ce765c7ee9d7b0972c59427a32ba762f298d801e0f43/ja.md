```
conv3dinputvertex(name, nchannel)
```

与えられた `name` を持つ入力タイプの頂点を返し、`nchannel` チャンネルを持つ畳み込み形状の入力を約束します。これは `Flux` の畳み込み層に適しています。

[`convinputvertex(name, nchannel, 3)`](@ref) と同等です。

入力タイプを提供することは、パッケージが機能するために厳密に必要ではなく、多くの場合、通常の `inputvertex` で十分です。

それが有用な例の一つは、入力タイプを知る必要がある [`concat`](@ref) 関数であり、自動的にどの次元を連結するかを決定します。
