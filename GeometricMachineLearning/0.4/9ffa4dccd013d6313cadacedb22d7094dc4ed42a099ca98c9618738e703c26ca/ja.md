```
StiefelProjection(backend, T, N, n)
```

特定のバックエンドとデータ型のために、$\begin{bmatrix} \mathbb{I} & \mathbb{O} \end{bmatrix}^T$の形の行列を作成します。

GPUサポートを持つ、実質的に`vcat(I(n), zeros(N-n, n))`を行う配列です。

# 拡張ヘルプ

`StiefelProjection`のインスタンスは、技術的には[`StiefelManifold`](@ref)にも属する必要があります。
