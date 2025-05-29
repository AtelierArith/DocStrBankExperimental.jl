```
summarize_table(::Val{:af_table})
```

| column_name | data_type       | unit                            | required | description                                                |
|:----------- |:--------------- |:------------------------------- |:-------- |:---------------------------------------------------------- |
| `area`      | AbstractString  | E4ST.NA                         | true     | フィルタリングに使用するエリア。つまり「州」。エリアでフィルタリングしない場合は空白のままにします。         |
| `subarea`   | AbstractString  | E4ST.NA                         | true     | フィルタに含めるサブエリア。つまり「メリーランド」。エリアでフィルタリングしない場合は空白のままにします。      |
| `genfuel`   | AbstractString  | E4ST.NA                         | true     | 発電機が使用する燃料タイプ。ジェンフューエルでフィルタリングしない場合は空白のままにします。             |
| `gentype`   | String          | E4ST.NA                         | true     | 発電機が使用する発電技術のタイプ。ジェンタイプでフィルタリングしない場合は空白のままにします。            |
| `year`      | E4ST.YearString | E4ST.Year                       | false    | AFを適用する年を、"y"で始まる年の文字列として表現します。つまり「y2022」                  |
| `status`    | Bool            | E4ST.NA                         | false    | このAF調整を使用するかどうか                                            |
| `h_`        | Float64         | E4ST.MWhGeneratedPerMWhCapacity | true     | 時間 _ の可用性係数。時間テーブルの各時間に1列を含めます。つまり `:h1`, `:h2`, ... `:hn` |
