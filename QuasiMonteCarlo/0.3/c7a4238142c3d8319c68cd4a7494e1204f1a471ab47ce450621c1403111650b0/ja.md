```
randomize(x, R::ScrambleMethod)
```

`x`のスクランブルされたバージョンを返します。実装されているスクランブル方法は次のとおりです。

  * `DigitalShift`.
  * `OwenScramble`: Owen (1995)で導入されたネストされた一様スクランブル。
  * `MatousekScramble`: Matousek (1998)で導入された線形行列スクランブル。
