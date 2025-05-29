```
BreuschGodfreyTest(X, e, lag, start0 = true)
```

回帰モデルの残差における系列相関のためのBreusch-Godfreyテストを計算します。

`X`は元のモデルからの回帰変数の行列で、`e`は残差のベクトルです。`lag`は補助回帰に含まれる遅延残差の数を決定します。`start0`を設定して、遅延残差の初期値の扱いを指定します。`start0 = true`（デフォルト）はそれらをゼロに設定します（Godfrey, 1978のように）；`start0 = false`は最初の`lag`残差を初期値として使用し、すなわちサンプルを`lag`だけ短縮します。

# 外部リンク

  * [Breusch-Godfrey test on Wikipedia](https://en.wikipedia.org/wiki/Breusch–Godfrey_test)

```
