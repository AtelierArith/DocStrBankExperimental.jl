```julia
remove!(tm::TextStyleModifier, key::Symbol)
```

`TextStyleModifier`から指定されたスタイル文字列を削除します。

```julia
using OliveHighlighters; TextStyleModifier, style_julia!
tm = TextStyleModifier("")
style_julia!(tm)

# クラスを確認:
classes(tm)

# クラスを削除:
remove!(tm, :default)
```

  * 参照: `set_text!`, `TextStyleModifier`, `clear!`
