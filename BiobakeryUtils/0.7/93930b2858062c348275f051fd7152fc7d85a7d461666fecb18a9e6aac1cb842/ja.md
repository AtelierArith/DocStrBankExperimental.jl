```
metaphlan_profile(path::AbstractString, rank::Union{Int, Symbol}=:all; sample::AbstractString=basename(first(splitext(path))))
```

MetaPhlAnの出力ファイルからCommunityProfileを作成します。分類学的ランクに応じてデータを選択できます。ランクが指定されていない場合は、すべてのデータが使用されます。CommunityProfileの`Sample name`は、`sample`引数を渡すことで指定できます。名前が指定されていない場合、ファイルの名前が`Sample name`になります。

レベルは数字またはシンボルで指定できます：

  * `1` = `:kingdom`
  * `2` = `:phylum`
  * `3` = `:class`
  * `4` = `:order`
  * `5` = `:family`
  * `6` = `:genus`
  * `7` = `:species`
  * `8` = `:subspecies`
