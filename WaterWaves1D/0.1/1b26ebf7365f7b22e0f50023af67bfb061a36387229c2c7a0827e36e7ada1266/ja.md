```
Data( m :: Matrix )
```

初期値問題の解を時間に沿って保存するためのデータ構造です。

`data=Data(m)`はパラメトリック型であり、次のことを提供します。

  * `data.U`は、行列`m`のコピーを持つ1要素ベクトルです；
  * `(data.datalength,data.datasize)=size(m)` ここで、`datalength`は計算されたモードの数であり、`datasize`は関与する方程式の数で、通常は2です。
