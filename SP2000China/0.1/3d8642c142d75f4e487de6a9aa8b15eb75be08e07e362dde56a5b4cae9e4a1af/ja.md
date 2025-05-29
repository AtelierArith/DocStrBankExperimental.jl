`GetFamiliesByFamilyName(;family_name::String,api_key::String,page::Int=1)`

# 説明

  * 家族名でクエリを実行し、家族IDのコレクションを返します。

# パラメータ

  * `family_name`: 家族名、またはその一部で、ラテン名と中国名の両方をサポートしています。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。
  * `page`: ページ番号、1以上の整数。指定しない場合は1がデフォルトとなります。

# 結果

  * `result`: `GetFamiliesByFamilyNameStruct`型の構造体。
  * `result.data`: JSON情報から変換された辞書。
  * `result.count`: 一致する総数。
  * `result.page`: 現在のデータページ。
  * `result.limit`: ページごとに表示されるアイテムの数。
  * `result.abstract`: 洗練されたデータフレーム。

# 例

```
using SP2000China;
your_family_name = "Coriariaceae";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = GetFamiliesByFamilyName(family_name=your_family_name,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
