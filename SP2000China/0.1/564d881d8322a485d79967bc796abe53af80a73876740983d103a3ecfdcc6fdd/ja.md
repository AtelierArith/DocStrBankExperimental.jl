`GetNameByKeyword(;keyword::String,api_key::String,page::Int=1)`

# 説明

  * キーワードに基づいて名前情報を検索します。

# パラメータ

  * `keyword`: 名前のキーワード（2文字以上）。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。
  * `page`: ページ番号、1以上の整数。指定しない場合は1がデフォルトです。

# 結果

  * `result`: `GetNameByKeywordStruct`型の構造体。
  * `result.data`: JSON情報から変換された辞書。
  * `result.count`: 一致する総数。
  * `result.page`: 現在のデータページ。
  * `result.limit`: ページごとに表示されるアイテムの数。
  * `result.abstract`: 洗練されたデータフレーム。

# 例

```
using SP2000China;
your_keyword="柳莺";
your_api_key = "アカウントを登録してAPIキーを取得してください";
your_page = 1;
result = GetNameByKeyword(keyword=your_keyword,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
