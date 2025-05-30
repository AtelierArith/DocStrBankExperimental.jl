A color input (`<input type="color">`) - ユーザーはRGBカラーを選択でき、色は`@bind`を介してカラーの16進数`String`として返されます。値は小文字で、`#`で始まります。

`default`を使用して初期値を設定します。

# 例

`@bind color ColorStringPicker()`

`@bind color ColorStringPicker(default="#aabbcc")`

# 参照

[`ColorPicker`](@ref)
