```
struct Keystorke
```

キー入力を定義する構造体です。

# フィールド

  * `value`: キー入力を表す文字列。
  * `ktype`: キーのタイプ（`:char`, `:F1`, `:up` など）。
  * `alt`: ALTキーが押された場合は `true`（`ktype != :char` の場合のみ有効）。
  * `ctrl`: CTRLキーが押された場合は `true`（`ktype != :char` の場合のみ有効）。
  * `shift`: SHIFTキーが押された場合は `true`（`ktype != :char` の場合のみ有効）。
