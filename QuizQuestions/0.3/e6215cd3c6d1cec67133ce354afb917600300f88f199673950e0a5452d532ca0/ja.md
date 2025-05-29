```
radioq(choices, answer; label="", hint="", explanation="", keep_order=false)
```

複数選択肢の質問（いくつかの中の1つ）

引数:

  * `choices`: 選択肢のインデックス可能なコレクション。例に示すように、選択肢はマークダウンでフォーマットできます。
  * `answer::Int`: 正しい選択肢のインデックス
  * `keep_order::Boolean`: `true`の場合、選択肢の表示順序を保持し、そうでない場合はシャッフルされます
  * `inline::Bool`: サポートされている場合、インラインでヒントをレンダリングするかどうか
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `explanation`: 間違った選択時に表示されるテキスト

## 例:

```
choices = ["beta", raw"``\beta``", "`beta`"]
answer = 2
radioq(choices, answer; hint="どれがギリシャ文字ですか？")
```
