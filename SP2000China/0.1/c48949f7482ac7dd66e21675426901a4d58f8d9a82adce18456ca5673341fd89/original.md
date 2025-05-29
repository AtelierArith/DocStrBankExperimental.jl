`DfSearch(;search_data::DataFrame,search_col::String,source_data::DataFrame,source_col::String)`

# Description

  * Searches for species based on a local database.

# Parameters

  * `search_data`: The DataFrame that needs to be searched.
  * `search_col`: The column name in the search DataFrame to look for.
  * `source_data`: The DataFrame of local data.
  * `source_col`: The column name in the local data DataFrame to look for.

# Results

  * `result`: The merged search results.

# Example

```
using SP2000China;
using SP2000ChinaData;
using DataFrames;
chinese_names = ["黄顶菊", "虚构植物", "爵床", "菖蒲", "慈姑", "野慈姑"];
sampling_points = ["西藏", "四川", "江苏", "湖北", "广东", "浙江"];
your_search_data = DataFrame(中文名=chinese_names, 采样点=sampling_points);
your_source_data = Plantae();
your_search_col = "中文名";
your_source_col = "物种中文名";
result = DfSearch(search_data=your_search_data,search_col=your_search_col,source_data=your_source_data,source_col=your_source_col);
println(result.matched)
println(result.unmatched)
```
