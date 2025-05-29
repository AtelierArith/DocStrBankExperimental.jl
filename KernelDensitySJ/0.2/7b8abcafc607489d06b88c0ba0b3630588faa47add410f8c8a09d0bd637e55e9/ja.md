```
GaussianKernelSmoother(x,y; leafSize=10)
```

座標 `x` と値 `y` を持つデータポイントのセットの `GaussianKernelSmoother` オブジェクトを作成します。注意: `x` と `y` への参照は GaussianKernelSmoother オブジェクトに保存されます。つまり、GaussianKernelSmoother を作成した後に `x` または `y` を変更すると、正しい結果が得られません。

他にも `smooth`、`density` を参照してください。
