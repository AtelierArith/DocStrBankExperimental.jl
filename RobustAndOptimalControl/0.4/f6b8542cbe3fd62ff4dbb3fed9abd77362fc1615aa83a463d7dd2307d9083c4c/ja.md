```
Pcl, S, CS, T = hinfsignals(P::ExtendedStateSpace, G::LTISystem, C::LTISystem)
```

拡張状態空間モデル、プラント、および見つかったコントローラを使用して、閉ループ伝達関数を抽出します。

  * `Pcl : w → z` : 入力から重み付けされた関数への変換
  * `S   : w → e` : 入力から誤差への変換
  * `CS  : w → u` : 入力から制御への変換
  * `T   : w → y` : 入力から出力への変換
