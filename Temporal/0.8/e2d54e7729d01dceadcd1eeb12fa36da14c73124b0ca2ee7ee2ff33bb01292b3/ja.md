QuandlからTSオブジェクトとして時系列データをダウンロードします。

```
quandl(code::String;
       from::String="",
       thru::String="",
       freq::Char='d',
       calc::String="none",
       sort::Char='a',
       rows::Int=0,
       auth::String=quandl_auth())::TS
```

# 引数

  * `code::String;`: クエリするためのquandlコード
  * `from::String=""`: データが開始する日付、形式はyyyy-mm-ddの文字列で表現
  * `thru::String=""`: データが続く終了日付、形式はyyyy-mm-ddの文字列で表現
  * `freq::Char='d'`: データが発生する頻度（'d', 'w', 'm', 'q', または 'a'のいずれか）
  * `calc::String="none"`: Quandlエンジンに渡される計算（"none", "diff", "rdiff", "cumul", または "normalize"のいずれか）
  * `sort::Char='a'`: 結果をソートする方向（'a'または'd'のいずれか）
  * `rows::Int=0`: クエリから返す行数（デフォルトはすべての行に対応）
  * `auth::String=quandl_auth()`: ユーザーアカウント専用のQuandl APIの認証トークン
