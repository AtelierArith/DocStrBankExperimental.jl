```
multibuttonq(choices, answers; label="", hint="", explanation="", keep_order=false)
```

ボタンと「完了」ボタンを使用して、ユーザーの入力が正しいかどうかを示す回答を表示する複数選択質問（ゼロ、1 *または* 複数の選択肢）。

引数:

  * `choices`: 選択肢のインデックス可能なコレクション。例に示すように、選択肢はマークダウンでフォーマットできます。
  * `answers::Vector{Int}`: 正しい選択肢のインデックス
  * `keep_order::Boolean`: `true` の場合、選択肢の表示順序を保持し、そうでない場合はシャッフルされます
  * `inline::Bool`: サポートされている場合、インラインでヒントをレンダリングするかどうか
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `explanation`: 誤った選択時に表示されるテキスト

## 例

```
choices = ["pear", "tomato", "banana"]
answers = [1,3]
multibuttonq(choices, answers; label="yellow foods", hint="not the red one!")
```
