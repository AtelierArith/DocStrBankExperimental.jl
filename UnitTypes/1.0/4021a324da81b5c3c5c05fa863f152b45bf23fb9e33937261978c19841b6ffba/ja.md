`macro makeMeasure(relation, unit="NoUnit", defineConverts=true)`

既存の基本測定から新しい測定を作成します。等式の左側はすでに存在している必要があり、右側は未定義である必要があり、末尾の文字列が単位記号を提供します。

`@makeMeasure Meter(1) = MilliMeter(1000) "mm"`

結果として得られる型は、`println(names(MyModule, all=true))`で見られるように、UnitTypesではなく、含まれているモジュールで定義されます。
