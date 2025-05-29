`FindUnknown(all_df::DataFrame)`

# 説明

  * テーブルから検索で見つからなかった種をフィルタリングします。

# パラメータ

  * `all_df`: `Chinese2Latin` 関数によって処理された後の結果。

# 結果

  * `result`: データベースで一致しなかった種がフィルタリングされます。一般名やその他の要因について考慮する必要があるかもしれません。

# 例

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
all_df = Chinese2Latin(chinese_data=your_chinese_data,col_name=your_col_name,api_key=your_api_key,page=your_page);
println(all_df)
result = FindUnknown(all_df);
println(result)
```
