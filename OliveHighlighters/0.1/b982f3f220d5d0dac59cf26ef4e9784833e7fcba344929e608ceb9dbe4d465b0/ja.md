```julia
classes(tm::TextStyleModifier) -> Base.Generator
```

`TextStyleModifier`で現在スタイルが適用されているクラスの`Tuple`ジェネレーターを返します。これは`styles`フィールドのキーを取得するのと同等です。`remove!`を使用してクラスを削除することもできます。（ジェネレーターを割り当てるには、単に`Vector`に提供してください）

```julia
using OliveHighlighters; TextStyleModifier, style_julia!
tm = TextStyleModifier("")
style_julia!(tm)

classes(tm)

# allocated:
my_classes = [classes(tm) ...]
```

  * 参照: `set_text!`, `TextStyleModifier`, `clear!`, `remove!(tm::TextStyleModifier, key::Symbol)`
