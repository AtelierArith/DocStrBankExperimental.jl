```
struct WelfareTable <: Modification
```

各年ごとの福祉に関する各項目の内訳を示すテーブルを出力します。

引数/キーワード引数：

  * name::Symbol
  * groupby - デフォルトでは空で、何もグループ化しません。州、郡などでグループ化することを選択できます。
