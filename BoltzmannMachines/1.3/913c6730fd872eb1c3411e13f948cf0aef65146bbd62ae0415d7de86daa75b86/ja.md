```
monitorweightsnorm!(monitor, rbm, epoch)
```

`rbm`の重み行列とバイアスベクトルのL2ノルムを計算し、その値を`monitor`に格納します。これらの値は、学習中にパラメータがどれだけ更新されているかの手がかりを与えることができます。
