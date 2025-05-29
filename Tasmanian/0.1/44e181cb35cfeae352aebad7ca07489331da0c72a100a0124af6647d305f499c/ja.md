```
copyGrid(tsg::TasmanianSG, outputs_begin = 0, outputs_end = -1)
```

は、TasmanianSparseGrid クラスのインスタンスを受け取り、クラスとすべての含まれるデータのハードコピーを作成します。元のクラスは変更されません。

tsg: TasmanianSG のインスタンス      コピーのソース

outputs_begin: コピーする最初の出力を示す整数

outputs*end: コピーする最後の出力よりも1大きい整数             -1に設定すると、outputs*beginから             終わりまでのすべての出力がコピーされます。

例:

copyGrid(other, 0, -1) # すべての出力をコピー (デフォルト) copyGrid(other, 0, getNumOutputs(other)) # すべてをコピー copyGrid(other, 0, 3) # 出力 0, 1, および 2 をコピー copyGrid(other, 1, 4) # 出力 1, 2, および 3 をコピー
