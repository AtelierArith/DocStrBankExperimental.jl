```
rff(X,m,σ)
```

ガウスカーネル行列のためのランダムフーリエ特徴 [rahimi2007random](@cite) を入力点 X とパラメータ σ に対して計算します。期待値として $\mathbf{MM}^t = \mathbf{K}$ となるランダム行列 M を返します。ここで、M は 2*m 列を持ちます。m が大きいほど、近似が良くなります。

## 例

```@example
x = randn(2, 10) #次元 2 の 10 点
rff(ColVecs(x), 4, 1.0)
```

関連情報: gaussker, kernelmatrix
