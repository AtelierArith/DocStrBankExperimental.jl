```
write_sphfile(fname, qs::Vector{SPHQPartition})
write_sphfile(fname, qs::SPHQPartition)
```

Q型球面波展開ファイルにSPH係数を書き込みます。

データをファイルに書き込む前に、入力係数（Q）は共役され、その後1/sqrt(8π)の因子で乗算されてQ′となり、Ticra標準の正規化と一貫性を持たせます。  
