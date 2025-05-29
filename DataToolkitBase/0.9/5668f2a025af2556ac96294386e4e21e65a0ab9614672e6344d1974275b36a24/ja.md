```
peelword(input::AbstractString)
```

`input`から次の「単語」を読み取ります。`input`が引用符で始まる場合、これは開き引用符と閉じ引用符の間のエスケープされていないテキストです。それ以外の場合は、単に次の単語です。

形式は`(word, rest)`のタプルを返します。

### 例

```julia-repl
julia> peelword("one two")
("one", "two")

julia> peelword(""one two" three")
("one two", "three")
```
