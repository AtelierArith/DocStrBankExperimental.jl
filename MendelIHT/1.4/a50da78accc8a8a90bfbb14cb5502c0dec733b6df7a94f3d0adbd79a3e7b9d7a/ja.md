```
score!(v::IHTVariable{T})
```

異なるGLMのためにスコア（勾配）`X^T * W * (y - g(x^T b))`を計算します。Wは対角行列であり、`w[i, i] = dμ/dη / var(μ)`です（ドキュメントを参照）。
