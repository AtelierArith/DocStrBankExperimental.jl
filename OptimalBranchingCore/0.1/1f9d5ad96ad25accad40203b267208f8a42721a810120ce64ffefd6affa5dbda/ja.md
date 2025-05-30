```
DNF{INT}
```

論理式を析出標準形（DNF）で表すデータ構造であり、これはリテラルの1つ以上の論理積の論理和です。OptimalBranchingCoreでは、DNFは分岐ルールを表すために使用されます。

# フィールド

  * `clauses::Vector{Clause{INT}}`: `Clause`オブジェクトのベクター。
