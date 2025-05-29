```
signal = getFlattenedSignal(signalTable, name;
                            missingToNaN = true,
                            targetInt    = Int,
                            targetFloat  = Float64)
```

信号のコピーを返します。ここで、*フラット化された*および*変換された*値（例：欠損 -> NaN）が `signal[:flattenedValues]` に保存され、凡例が `signal[:legend]` に保存されます。フラット化された信号は、例えば、従来のプロット関数や従来のテーブルに使用できます。

`signal[:flattenedValues]` は、値をベクトルまたは行列に再形成したもので、オプションで以下の変換が行われます：

  * `name` は、配列範囲インデックスの有無にかかわらず信号名であることができます（例えば `name = "a.b.c[2,3:5]"`）。
  * `missingToNaN=true` の場合、欠損値はNaN値に置き換えられます。対応する型にNaNが存在しない場合、値は最初に `targetFloat` に変換されます。
  * `targetInt` が何も指定されていない場合、Int型は `targetInt` に変換されます。
  * `targetFloat` が何も指定されていない場合、Float型は `targetFloat` に変換されます。
  * 結果に対して `collect(..)` が実行されます。

`flattenedSignal[:legend]` は、各配列列の説明を提供する文字列のベクトルです（例：`"name=a.b.c[2,3:5]", unit="m/s"` の場合、`legend = ["a.b.c[2,3] [m/s]", "a.b.c[2,3] [m/s]", "a.b.c[2,5] [m/s]"]`）。

必要な変換が不可能な場合、警告メッセージが表示され、`nothing` が返されます。

特別なケースとして、`signal[:values]` がベクトルであるか、`signal[:value]` がスカラーであり、値または値の要素が `Measurements{targetFloat}` または `MonteCarloMeasurements{targetFloat}` 型である場合、信号は変換されず、`signal[:flattenedValues] = signal[:values]` となります。
