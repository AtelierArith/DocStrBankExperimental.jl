`Chinese2Latin(;chinese_data::DataFrame,col_name::String,api_key::String,page::Int=1)`

# Description

  * Based on the species Chinese name column provided by the data frame, batch query the scientific names.

# Parameters

  * `chinese_data`: The data frame containing the species' Chinese names.
  * `col_name`: The name of the column in the data frame where the Chinese names are located.
  * `api_key`: The API service key for registered users.
  * `page`: The page number, an integer not less than 1. If not provided, it defaults to 1.

# Results

  * `result`: The data frame that summarizes the basic information after batch querying the Chinese names, with unknown displayed for content that could not be queried.

# Example

```
using SP2000China;
using DataFrames;
chinese_names = ["黄顶菊", "虚构植物", "爵床", "菖蒲", "慈姑", "野慈姑"];
sampling_point = ["西藏", "四川", "江苏", "湖北", "广东", "浙江"];
your_chinese_data = DataFrame(中文名=chinese_names, 采样点=sampling_point);
println(your_chinese_data)
your_col_name = "中文名";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = Chinese2Latin(chinese_data=your_chinese_data,col_name=your_col_name,api_key=your_api_key,page=your_page);
println(result)
```
