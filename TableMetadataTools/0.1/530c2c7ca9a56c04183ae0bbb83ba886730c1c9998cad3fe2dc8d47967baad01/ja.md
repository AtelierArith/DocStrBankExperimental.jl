```
@track ex
```

実行して `ex` の値を返し、`ex` の値の親に `:note` スタイルのテーブルレベルメタデータを追加します。キーは `"track_"` に実行時間を付加したもので、`Dates.now()` によって返されます（重複キーが存在する場合は `"_"` サフィックスがキーに追加されます）で、値は `ex` の文字列表現です。

このマクロはデータフレーム処理パイプラインの系譜を可能にするためのものです。

参照: [`tracklog`]

# 例

```
julia> using DataFrames

julia> df = DataFrame(a=1:3)
3×1 DataFrame
 Row │ a
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3

julia> @track agg = combine(df, :a => sum)
1×1 DataFrame
 Row │ a_sum
     │ Int64
─────┼───────
   1 │     6

julia> print(meta2toml(agg))
style = true

[colmetadata]

[metadata]
"track_2022-11-13T21:18:47.359" = ["agg = combine(df, :a => sum)", "note"]
```
