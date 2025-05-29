```
multiq(choices, answers; label="", hint="", explanation="", keep_order=false)
```

複数選択式質問（いくつかの中から*1つ以上*）

引数:

  * `choices`: 選択肢のインデックス可能なコレクション。例に示すように、選択肢はマークダウンでフォーマットできます。
  * `answers::Vector{Int}`: 正しい選択肢のインデックス
  * `keep_order::Boolean`: `true`の場合、選択肢の表示順序を保持し、そうでない場合はシャッフルされます
  * `inline::Bool`: サポートされている場合、インラインで表示するヒント（またはしない）
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `explanation`: 誤った選択時に表示されるテキスト

## 例

```
choices = ["pear", "tomato", "banana"]
answers = [1,3]
multiq(choices, answers; label="黄色の食べ物", hint="赤いのではない！")
```
