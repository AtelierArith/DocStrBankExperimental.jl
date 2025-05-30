A color input (`<input type="color">`) - ユーザーはRGBカラーを選択でき、色は`@bind`を介してカラーHEX `String`として返されます。値は小文字で、`#`で始まります。

`default`を使用して初期値を設定します。

[Mozillaの`<input type="color">`に関するドキュメント](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/color)を参照してください。

# 例

`@bind color ColorStringPicker()`

`@bind color ColorStringPicker(default="#aabbcc")`
