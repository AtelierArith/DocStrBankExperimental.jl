```
InputData(name::Symbol, option::Symbol, data::Any)
```

より構造化された入力データのブロックを表します。例えば、`InputData(:k_points, :automatic, (6,6,6,1,1,1))` はQE計算のために次のように翻訳されます。

```
K_POINTS(automatic)
6 6 6 1 1 1
```
