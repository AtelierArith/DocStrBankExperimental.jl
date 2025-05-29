`GetSpeciesByScientificName(;scientific_name::String,api_key::String,page::Int=1)`

# 説明

  * 科学名でクエリを実行し、種のIDを返します。

# パラメータ

  * `scientific_name`: 科学名、またはその一部で、ラテン語と中国語の両方の名前をサポートします。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。
  * `page`: ページ番号、1以上の整数。指定しない場合は、デフォルトで1になります。

# 結果

  * `result`: `GetSpeciesByScientificNameStruct`型の構造体。
  * `result.data`: JSON情報から変換された辞書。
  * `result.count`: 一致する総数。
  * `result.page`: 現在のデータページ。
  * `result.limit`: ページごとに表示されるアイテムの数。
  * `result.abstract`: 洗練されたデータフレーム。

# 例

```
using SP2000China;
your_scientific_name = "Actinidia arg";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = GetSpeciesByScientificName(scientific_name=your_scientific_name,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
