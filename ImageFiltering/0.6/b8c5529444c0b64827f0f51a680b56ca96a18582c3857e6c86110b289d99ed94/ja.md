```julia
    Pad(style, kernel)
    Pad(style)(kernel)
```

[`Pad`](@ref) のインスタンスを、値 `val` とフィルター配列 `kernel` を指定して構築します。これにより、`kernel` の `axes` からのパディングの量が決定されます。

#### 使用例

`Pad(:circular,Kernel.sobel())` を使用して、`:circular` ボーダースタイルと、画像の境界で [`Kernel.sobel`](@ref) との畳み込みが定義されるために必要な最小限のパディング量を指定します。

---
