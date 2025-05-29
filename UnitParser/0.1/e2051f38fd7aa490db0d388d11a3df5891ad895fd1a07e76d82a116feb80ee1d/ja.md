```
short_form(unit_name::AstractString)
```

単位の自然名を接頭辞と名前の記号形式に短縮します。

一致が見つからない場合は、元の文字列を返します。

# 例

julia> short_form("micrometers") ("μ", "m")

# 戻り値

unit_prefix: String     単位の接頭辞を表す短縮形、例えば「k」は「キロ」を表します。単位に接頭辞がない場合は空の文字列に設定されます。

core_unit: String     単位を表す短縮形、例えば「A」は「アンペア」を表します。 ```
