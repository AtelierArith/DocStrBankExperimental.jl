```
ChebyshevInterpolator(x, y)
```

座標 `x` と値 `y` で定義された点のための `ChebyshevInterpolator` を構築します。`x` 座標は *必ず* チェビシェフグリッド上に配置されている必要があり、これは [`chebygrid`](@ref) 関数を使用して生成できます。
