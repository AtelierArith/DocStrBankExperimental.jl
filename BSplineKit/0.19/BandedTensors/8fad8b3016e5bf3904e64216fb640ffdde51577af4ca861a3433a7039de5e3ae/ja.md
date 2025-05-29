```
bandwidth(A::BandedTensor3D)
```

[`BandedTensor3D`](@ref)のバンド幅`b`を取得します。

バンド幅はここで定義されており、要素`A[i, j, k]`は$|i - j| ≤ b$、$|i - k| ≤ b$、および$|j - k| ≤ b$の場合にのみ非ゼロである可能性があります。この定義は、`BandedMatrices`における上部および下部バンド幅の仕様と一致しています。
