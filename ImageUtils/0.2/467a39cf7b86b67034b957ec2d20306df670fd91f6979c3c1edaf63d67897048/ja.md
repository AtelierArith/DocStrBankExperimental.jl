```
CBF_maxgrad(tseries::ImageMeta[;positionArtery=[1,1,1], alpha=0.4, alpha2=2,windowsize=6])
```

マスク内のピクセルに対して時間的次元に沿った最大勾配をピクセル単位で計算し、動脈の位置での最大濃度で割ります。代替: CBFはCBV/MTTの比率から脳血流を計算します。
