与えられたテキストと引用グループに一致する正規表現（例：pandocなど）を使用して、そのテキスト内から引用グループのベクターを抽出して返します。

## 引数

  * `text::String` - 処理されるテキスト

## キーワード引数

  * `key_regex::Regex` - 引用グループをキャプチャするための正規表現；デフォルトは、`[@citation]` または `[@citation_1; @citation_2]` の形式の引用キーグループをキャプチャします。

## 戻り値

  * キャプチャされた引用キーグループの文字列のベクター
