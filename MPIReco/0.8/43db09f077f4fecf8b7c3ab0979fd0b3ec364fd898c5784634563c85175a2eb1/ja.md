```
findPeaks(data; stdTh=1.5, minBinDist=0, minBin=1)
```

データ内のピークを見つけます。

  * data:         データの列ベクトル
  * stdTh:        ピークは平均値よりも少なくとも stdTh*標準偏差 高い
  * minBinDist:   2つのピークの間の最小ビン数
  * minBin:       minBin 未満のビンにはピークがない
  * return:       ピークビン
