```
latex_symbol(
            mid::String;
            sub::String = "",
            sup::String = "",
            presub::String = "",
            presup::String = "",
            option::String = "mathrm"
)
```

次の引数に基づいてlatexシンボル文字列を返します。

  * `mid` 中心シンボル、長さが1より大きい場合はイタリック
  * `sub` オプション: `mid` の後の下付き文字
  * `sup` オプション: `mid` の後の上付き文字
  * `presub` オプション: `mid` の前の下付き文字
  * `presup` オプション: `mid` の前の上付き文字
  * `option` オプション: `text` と `mathrm` から選択（デフォルト）
