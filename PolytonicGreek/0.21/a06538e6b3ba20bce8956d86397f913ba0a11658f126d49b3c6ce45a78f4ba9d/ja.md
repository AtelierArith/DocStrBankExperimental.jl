文字列 `s` を音節を表す文字列の配列に分割します。

```julia
syllabify(s, ortho)

```

# 例

```jldoctest
syllables = PolytonicGreek.syllabify("κελεύει")
join(syllables, "-")
"κε-λευ-ει"
```
