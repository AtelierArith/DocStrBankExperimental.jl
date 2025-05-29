```
matchq(questions, choices, answers; label="", hint="", explanation="")
matchq(d::Dictionary; label="", hint="", explanation="")
```

各質問に対して正しいマッチを選択するためにドロップダウンを使用します。

引数:

  * `questions`: 質問のインデックス可能なコレクション
  * `choices`: 各質問の選択肢のインデックス可能なコレクション。例に示すように、選択肢はマークダウンでフォーマットできます。
  * `answers`: 各質問に対して、正しい答えの`choices`からのインデックス
  * `d`: 代わりに、質問と答えの辞書を指定できます。選択肢は値から取得され、その後ランダム化され、答えが計算されます
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `explanation`: 間違った選択に対して表示されるテキスト

## 例

```
questions = ("ボルボを選択", "メルセデスを選択", "アウディを選択")
choices = ("XC90", "A4", "GLE 350", "X1") # 質問より多くなる場合があります
answer = (1,3,2) # 正しいインデックス
matchq(questions, choices, answer)
```

この例では、辞書を使用して質問と選択肢を指定します:

```
d = Dict("ボルボを選択" => "XC90", "メルセデスを選択" => "GLE 250")
matchq(d)
```
