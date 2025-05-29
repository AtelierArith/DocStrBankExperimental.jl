`GetSpeciesByFamilyId(;family_id::String,api_key::String,page::Int=1)`

# 説明

  * 科IDによって種をクエリし、種のリストを返します。

# パラメータ

  * `family_id`: 科ID、ユニークな値。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。
  * `page`: ページ番号、1以上の整数。提供されない場合はデフォルトで1になります。

# 結果

  * `result`: `GetSpeciesByFamilyIdStruct`型の構造体。
  * `result.data`: JSON情報から変換された辞書。
  * `result.count`: 一致する総数。
  * `result.page`: 現在のデータページ。
  * `result.limit`: ページごとに表示されるアイテムの数。
  * `result.abstract`: 洗練されたデータフレーム。

# 例

```
using SP2000China;
your_family_id = "F20171000000291";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = GetSpeciesByFamilyId(family_id=your_family_id,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
