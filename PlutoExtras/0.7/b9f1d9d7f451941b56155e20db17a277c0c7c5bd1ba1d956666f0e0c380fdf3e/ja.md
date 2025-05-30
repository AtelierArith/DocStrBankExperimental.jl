```
Editable(x::Real; [prefix, suffix, format])
```

`Scrubbable`(@ref)と同様のPlutoウィジェットを作成しますが、入力として任意の（Real）数値を含むことができます。

表示されるHTMLは、青い背景を持つspanを作成し、その中に数値が含まれ、オプションのテキスト`prefix`とオプションのテキスト`suffix`が前に置かれます。`format`が指定されている場合、それは表示される数値を[ダ3フォーマット](https://github.com/d3/d3-format#locale_format)仕様を使用してフォーマットするために使用されます。

ウィジェットは、Enterキーを押すか、ウィジェット自体からフォーカスを移動させたときのみ、ボンドの更新をトリガーします。

![79f77981-2c53-4ff0-bd13-8213519e0bca](https://github.com/disberd/PlutoExtras.jl/assets/12846528/cb0f19e3-7dcb-46d6-88b1-1bbe1592dd1c)

# キーワード引数

  * `prefix::AbstractString`: 表示されるHTMLの数値の前に挿入される文字列。サフィックスをクリックすると、数値を定義する完全なテキストが選択されます
  * `suffix::AbstractString`: 表示されるHTMLの数値の後に挿入される文字列。サフィックスをクリックすると、数値を定義する完全なテキストが選択されます
  * `format::AbstractString`: HTMLで数値を表示するために使用するフォーマットを指定する文字列。[ダ3フォーマット](https://github.com/d3/d3-format#locale_format)仕様を使用します
