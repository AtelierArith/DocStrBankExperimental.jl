```
stringq(re::Regex; filter::Regex=r"", label="", hint="", explanation="", placeholder="")
```

正規表現で文字列の回答を一致させる

引数:

  * `re`: 採点用の正規表現
  * `filter`: 一致させる前に文字列から削除するための正規表現（例: `r"\s"` は空白を削除）
  * `label`: フォーム要素のオプションラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `explanation`: 不正な選択時に表示されるテキスト
  * `placeholder`: 入力ウィジェットが最初に描画されたときに表示されるテキスト

## 例

```
re = Regex("^abc")
stringq(re, label="最初の3文字...")
```
