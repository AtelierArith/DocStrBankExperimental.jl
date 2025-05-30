```
csm(t;n=1024,noverlap=div(n,2),fs=1,win=DSP.hanning(n),scaling="spectrum")
```

時間系列`t`からクロススペクトル行列を計算します。`t`は`S x M`次元で、`S`はサンプル数、`M`はマイクの数です。
