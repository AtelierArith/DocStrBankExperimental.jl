`Chinese2Latin(;chinese_data::DataFrame,col_name::String,api_key::String,page::Int=1)`

# 説明

  * データフレームで提供された種の中国名の列に基づいて、科学名をバッチで照会します。

# パラメータ

  * `chinese_data`: 種の中国名を含むデータフレーム。
  * `col_name`: データフレーム内の中国名がある列の名前。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。
  * `page`: ページ番号、1以上の整数。指定がない場合は1がデフォルトです。

# 結果

  * `result`: 中国名をバッチ照会した後の基本情報を要約したデータフレームで、照会できなかった内容は不明として表示されます。

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
result = Chinese2Latin(chinese_data=your_chinese_data,col_name=your_col_name,api_key=your_api_key,page=your_page);
println(result)
```
