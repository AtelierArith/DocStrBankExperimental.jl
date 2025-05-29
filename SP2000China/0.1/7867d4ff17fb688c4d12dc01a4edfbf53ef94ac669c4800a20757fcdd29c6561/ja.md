`StrSearch(;search_str::String,source_data::DataFrame,source_col::String)`

# 説明

  * ローカルデータベースに基づいて種を検索します。

# パラメータ

  * `search_str`: 検索する必要がある文字列。
  * `source_data`: ローカルデータのDataFrame。
  * `source_col`: ローカルデータのDataFrameで探す列名。

# 結果

  * `result`: 結合された検索結果。

# 例

```
using SP2000China;
using SP2000ChinaData;
your_search_str = "慈姑";
your_source_data = Plantae();
your_source_col = "物种中文名";
result = StrSearch(search_str=your_search_str,source_data=your_source_data,source_col=your_source_col);
println(result)
```
