```
numericq(value, atol=1e-3; label="", hint="", units="", explanation="", placeholder=nothing)
```

数値回答を一致させる

引数:

  * `value`: 数値回答
  * `atol`: $|\mathrm{answer} - \mathrm{value}| \le \mathrm{atol}$ は正しさを判断するために使用されます
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `units`: 期待される単位を示す文字列
  * `placeholder`: 入力ウィジェットが最初に描画されたときに表示されるテキスト
