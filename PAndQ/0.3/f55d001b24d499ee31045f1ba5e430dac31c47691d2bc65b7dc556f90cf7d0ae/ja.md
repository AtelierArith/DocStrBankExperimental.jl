```
interpret(valuation, p)
```

`p`の各原子を`valuation`によって与えられた値で置き換えます。

`valuation`は、原子を受け取り論理値を返す`Function`、原子から論理値へのマッピングを持つ`Dict`、またはそのような辞書を構築できる反復可能なオブジェクトである可能性があります。原子が辞書のキーの1つでない場合、置き換えは行われません。

# 例

```jldoctest
julia> @atomize interpret(atom -> ⊤, ¬p)
¬⊤

julia> @atomize interpret(p => ⊤, p ∧ q)
⊤ ∧ q
```
