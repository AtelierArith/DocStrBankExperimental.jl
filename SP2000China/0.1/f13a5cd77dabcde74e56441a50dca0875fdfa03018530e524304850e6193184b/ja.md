`GetSpeciesByCommonName(;common_name::String,api_key::String,page::Int=1)`

# 説明

  * 一般名でクエリを実行し、種または亜種の情報を返します。

# パラメータ

  * `common_name`: 一般名、またはその一部。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。
  * `page`: ページ番号、1以上の整数。指定しない場合は1がデフォルトとなります。

# 結果

  * `result`: `GetSpeciesByCommonNameStruct`型の構造体。
  * `result.data`: JSON情報から変換された辞書。
  * `result.count`: 一致する総数。
  * `result.page`: 現在のデータページ。
  * `result.limit`: ページごとに表示されるアイテムの数。
  * `result.abstract`: 洗練されたデータフレーム。

# 例

```
using SP2000China;
your_common_name = "土人参";
your_api_key = "アカウントを登録してAPIキーを取得してください";
your_page = 1;
result = GetSpeciesByCommonName(common_name=your_common_name,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
