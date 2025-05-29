```
cross(data::PopData, parent1::String, parent2::String; n::Int = 100, generation::String = "F1")
```

`PopData`オブジェクトからの個体`parent1`と`parent2`の間の繁殖交配をシミュレートします。交配から得られた`n`の子孫を含むPopDataを返します。

#### キーワード引数

  * `n` : 生成する子孫の数の整数（デフォルト: `100`）
  * `generation` : 子孫に`population`の識別子を割り当てるための文字列（デフォルト: `"F1"`）
