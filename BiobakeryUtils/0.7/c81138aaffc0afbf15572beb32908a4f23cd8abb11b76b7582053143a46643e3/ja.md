```
metaphlan_profiles(path::AbstractString, rank::Union{Int, Symbol}=:all; keepunidentified=false)
```

MetaPhlAnプロファイルをマージされたテーブルからCommunityProfileに読み込みます。分類学的ランクに応じてデータを選択できます。ランクが指定されていない場合は、すべてのデータが使用されます。`keepunidentified`フラグを`true`に設定すると、`UNIDENTIFIED`データを保持します。

レベルは数字またはシンボルのいずれかで指定できます：

  * `1` = `:kingdom`
  * `2` = `:phylum`
  * `3` = `:class`
  * `4` = `:order`
  * `5` = `:family`
  * `6` = `:genus`
  * `7` = `:species`
  * `8` = `:subspecies`
