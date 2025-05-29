`StrSearch(;search_str::String,source_data::DataFrame,source_col::String)`

# Description

  * Searches for species based on a local database.

# Parameters

  * `search_str`: The string that needs to be searched.
  * `source_data`: The DataFrame of local data.
  * `source_col`: The column name in the local data DataFrame to look for.

# Results

  * `result`: The merged search results.

# Example

```
using SP2000China;
using SP2000ChinaData;
your_search_str = "慈姑";
your_source_data = Plantae();
your_source_col = "物种中文名";
result = StrSearch(search_str=your_search_str,source_data=your_source_data,source_col=your_source_col);
println(result)
```
