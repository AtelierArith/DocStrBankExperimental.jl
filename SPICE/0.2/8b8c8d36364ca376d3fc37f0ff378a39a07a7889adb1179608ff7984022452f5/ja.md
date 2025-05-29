```
kxtrct(keywd, terms, string)
```

キーワードを文字列内で見つけ、キーワードに続く最初の単語の始まりから、リストの最初の認識された終端子の始まりまでの部分文字列を抽出します。

### 引数

  * `keywd`: 興味のあるテキストの始まりを示す単語
  * `terms`: テキストの終わりを示す単語のセット
  * `string`: 単語のシーケンスを含む文字列

### 出力

`keywd` が見つかった場合は `nothing` を返し、そうでない場合は次の要素からなるタプルを返します。

  * `string`: 興味のあるテキストが削除された入力 `string`
  * `substr`: `keywd` の終わりから最初に見つかった `terms` アイテムの始まりまでの文字列

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/kxtrct_c.html)
