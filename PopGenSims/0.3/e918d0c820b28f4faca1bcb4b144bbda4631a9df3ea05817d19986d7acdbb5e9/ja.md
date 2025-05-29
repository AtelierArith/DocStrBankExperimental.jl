```
cross(parent_1::Pair, parent_2::Pair, n::Int = 100, generation::String = "F1")
```

異なる `PopData` オブジェクトからの個体 `parent` と `parent2` の間で繁殖交配をシミュレートします。交配から得られる `n` の子孫を含む PopData を返します。`parent_1_data` と `parent_2_data` は位置引数であるため、キーワードなしで、親1、親2の順に記述する必要があります。

#### キーワード引数

  * `parent_1` : `PopData => "Parent1Name"` のペア
  * `parent_2` : `PopData => "Parent1Name"` のペア
  * `n` : 生成する子孫の数の整数 (デフォルト: `100`)
  * `generation` : 子孫に `population` の識別子と名前の接頭辞を割り当てるための文字列 (デフォルト: `"F1"`)
