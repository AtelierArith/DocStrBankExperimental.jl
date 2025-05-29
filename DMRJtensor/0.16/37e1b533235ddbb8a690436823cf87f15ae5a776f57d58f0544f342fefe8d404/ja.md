```
rho = correlationmatrix(dualpsi,psi,Cc,Ca[,F,silent=])
```

すべてのサイトで相関関数（例、<`dualpsi`|`Cc`*i . `Ca`*j|`psi`>）を計算します。フェルミオン文字列のためにトレイル `F` を指定することもできます。`silent` は各行の出力を切り替えます。出力は行列 `rho` です。

# 注:

  * `mpoterm` や `correlation` を使用するよりも効率的です。
  * より高次の相関関数には `mpoterm` と `applyMPO` を使用するか、新しい関数を書くことを検討してください。
