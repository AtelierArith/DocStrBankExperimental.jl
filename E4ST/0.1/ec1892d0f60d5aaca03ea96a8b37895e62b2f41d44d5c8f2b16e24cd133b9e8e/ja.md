```
match_nominal_load!(config, data)
```

`config[:load_match_file]` に示された地域ごとの年間負荷を一致させ、`data[:bus]` の `pd` フィールドを更新します。詳細については [`summarize_table(::Val{:load_match})`](@ref) を参照してください。

多くの場合、データソースからの負荷予測に一致させるために、年間を通じて一連の負荷要素の総エネルギー負荷を強制したいと考えます。`load_match_table` は、ユーザーが一致させるための年間エネルギー負荷目標を $MWh$ 単位で提供できるようにします。一致させる際には、各代表的な時間で過ごした時間数によって各時間の負荷に重みを付け、代表的な時間の $MW$ 電力負荷から $MWh$ に変換します。
