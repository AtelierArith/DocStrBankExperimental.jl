```
Encoding(x; channels...)
Encoding(x, y; channels...)
Encoding(; channels...)
```

単一またはレイヤービュー仕様の `encoding` プロパティを含む `EncodingSpec` を作成します。 `x` および `y` チャンネルは、ショートハンド文字列構文を使用して位置引数として指定できます。詳細は [Vega-Lite's](https://vega.github.io/vega-lite/docs/encoding.html) と [Deneb.jl's](https://brucala.github.io/Deneb.jl/dev/data_mark_encoding/#Encoding) を参照してください。

# 例

```
Encoding("monthdate(date):T", "mean(precipitation):Q", color="year(date):O")
Encoding(
    x=field("bin_min:Q", bin=:binned, title="最大日温度 (C)"),
    y=field("value:Q", scale=(range=[20, -20]), axis=nothing),
    fill=field="mean_temp:Q",
)
```
