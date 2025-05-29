```
gaussker(X,σ)
```

点Xとパラメータσに対するガウスカーネル行列を計算します。すなわち、エントリi,jが$\exp(-\frac{(x_i-x_j)^2}{2σ^2})$に等しい行列です。

σが指定されていない場合、中央値ヒューリスティックを使用して設定されます。点の数が非常に多い場合、中央値はランダムなサブセットで推定されます。

```@example
x = randn(2, 6)
gaussker(ColVecs(x), 0.1)
```

関連情報: rff, KernelMatrix:kernelmatrix
