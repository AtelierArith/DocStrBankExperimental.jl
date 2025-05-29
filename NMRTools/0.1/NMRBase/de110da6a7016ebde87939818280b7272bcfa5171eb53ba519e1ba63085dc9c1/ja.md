```
GaussWindow(expHz, gaussHz, center, tmax)
```

ローレンツからガウスウィンドウ関数の抽象表現であり、`expHz` Hzの逆指数関数と、`gaussHz` Hzのガウスの広がりを適用し、最大値は`center`（0と1の間）にあります。取得時間は`tmax`です。

`center`がゼロのときは`LorentzToGaussWindow`に特化し、それ以外の場合は`GeneralGaussWindow`になります。
