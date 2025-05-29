```
simulate_forward(eventHistory, maxT, startT, bg, kappa, kern)
```

既にいくつかのイベントを観測したことを前提に、ホークス過程をシミュレートします。これは将来のイベントを予測するために使用できます。

# 引数

  * `eventHistory` これまでに発生したイベント。
  * `maxT` シミュレーションを行う最大時間値。
  * `startT` シミュレーションを開始する時間。
  * `bg` バックグラウンド値
  * `kappa` カッパ値
  * `kern` カーネル関数または分布
