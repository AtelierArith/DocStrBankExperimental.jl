```
buttonq(choices, answer; label="", hint="", [colors])
```

複数選択肢のボタンを使用します（多くの中の1つ）。最初のクリック後に答えを表示します。

引数:

  * `choices`: 選択肢のインデックス可能なコレクション。例に示すように、選択肢はマークダウンでフォーマットできます。
  * `answer::Int`: 正しい選択肢のインデックス
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストのヒント
  * `explanation`: 誤った選択時に表示するテキスト
  * `colors` `GREEN`、`RED`、および `BLUE` の色を持つ名前付きタプル

## 例:

```
choices = ["beta", raw"``\beta``", "`beta`"]
answer = 2
explanation = "他の2つの答えは記号ではなく、名前です"
buttonq(choices, answer; label="どれがギリシャ文字ですか？",
        explanation=explanation)
```
