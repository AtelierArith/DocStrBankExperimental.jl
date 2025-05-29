```
parsetaxon(taxstring::AbstractString, rank::Union{Int, Symbol})
```

与えられた分類学的ランクを文字列内で見つけます（MetaPhlAnによってフォーマットされたもの、例："k**Bacteria|p**Proteobacteria..."）そして、名前と分類学的ランクを`Taxon`として返します。分類学的ランクが指定されていない場合、関数は利用可能な最も特定的（最も低い）分類学的ランクを返します。

レベルは数字またはシンボルのいずれかで指定できます：

  * `1` = `:kingdom`
  * `2` = `:phylum`
  * `3` = `:class`
  * `4` = `:order`
  * `5` = `:family`
  * `6` = `:genus`
  * `7` = `:species`
  * `8` = `:subspecies`

```
