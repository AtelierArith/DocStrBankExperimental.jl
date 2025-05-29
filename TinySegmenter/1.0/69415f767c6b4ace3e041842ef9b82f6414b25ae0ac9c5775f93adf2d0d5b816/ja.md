TinySegmenterモジュールは、文字列の日本語テキストをトークンを表す部分文字列の配列に分割するための関数`tokenize`を提供します：

```
using TinySegmenter

join(tokenize("私の名前は中野です"), " | ")
# "私 | の | 名前 | は | 中野 | です"
```
