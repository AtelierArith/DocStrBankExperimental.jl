```
Label(lbl::Symbol) :: Query
```

これは出力にラベルを割り当てます。

```jldoctest
julia> unitknot[Lift("Hello World") >> Label(:greeting)]
│ greeting    │
┼─────────────┼
│ Hello World │
```

ラベルは `=>` 演算子を使用しても割り当てることができます。

```jldoctest
julia> unitknot[:greeting => Lift("Hello World")]
│ greeting    │
┼─────────────┼
│ Hello World │
```
