```
parse_tor_struct(s::AbstractString) -> t::NamedTuple
```

入力文字列は、`TorObj`の`propval`フィールドのエントリであり、例えば「struct(status: automatic, x: 1 in, y:23.4  mm)」のような形式です。この関数はTicra構造体を解析し、Ticra構造体のフィールド名を持つ`NamedTuple` `t`を返します。`t`の`values`は文字列または`Unitful`量です。与えられた例では、`t.status == "automatic"`、`t.x == 1.0u"inch"`、および`t.y == 23.4u"mm"`です。
