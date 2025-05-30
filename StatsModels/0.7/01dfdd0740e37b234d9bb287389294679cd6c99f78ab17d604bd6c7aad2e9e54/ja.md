```
termnames(t::FormulaTerm)
```

式の左辺と右辺に適用された `termnames` の二重タプルを返します。

!!! note
    `apply_schema` が呼び出されるまで、式中のリテラル `1` は `ConstantTerm(1)` と解釈され、返される項名には `"1"` として表示されます。


```jldoctest
julia> termnames(@formula(y ~ 1 + x * y + (1+x|g)))
("y", ["1", "x", "y", "x & y", "(1 + x) | g"])
```

同様に、暗黙の切片を持つ式は、暗黙の切片が `apply_schema` が呼び出されるまで存在しないため、変数名に `"1"` を持ちません（特定のモデルコンテキストでは存在しない場合もあります）。

```jldoctest
julia> termnames(@formula(y ~ x * y + (1+x|g)))
("y", ["x", "y", "x & y", "(1 + x) | g"])
```
