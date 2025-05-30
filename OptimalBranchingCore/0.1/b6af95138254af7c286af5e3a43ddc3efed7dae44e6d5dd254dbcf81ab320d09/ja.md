```
Clause{INT <: Integer}
```

Clauseはリテラルの論理積であり、ビット列のペアによって指定されます。型パラメータ`INT`はビット列を格納するための整数型です。

### フィールド

  * `mask`: 句に関与する変数を示すビット列。
  * `val`: 句における正のリテラルを示すビット列。

### 例

ビット列が句を満たすかどうかを確認するには、`OptimalBranchingCore.covered_by`を使用します。

```jldoctest
julia> using OptimalBranchingCore

julia> clause = Clause(0b1110, 0b1010)
Clause{UInt8}: #2 ∧ ¬#3 ∧ #4

julia> OptimalBranchingCore.covered_by(0b1110, clause)
false

julia> OptimalBranchingCore.covered_by(0b1010, clause)
true
```
