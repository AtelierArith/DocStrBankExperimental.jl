```
output(::Simulation, [ filename => measure1, ... ])
```

シミュレーションで指定された測定値を計算し、それらを関連付けられたファイルまたは辞書に出力します。

ファイル名は get*sim*file によって解釈されます（特別な値についてはそこを参照してください）。

# 例

```
output(sim, "file" => [X, X(1)Y(2), (X, Y)])
output(sim, [ "file1" => [X, Y(2)], "file2" => Trace])
```
