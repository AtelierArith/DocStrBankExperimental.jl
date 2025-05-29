```
TeXChar(char, font)
```

関連するフォントを持つMathTeX文字。

TeXCharはFreeTypeAbstraction.FontExtentsのために定義されたすべての関数を実装しており、文字に関するすべての幾何学的情報を取得するために代わりに使用できます。

これは、数式記号の適切な位置決めのために調整が必要なフォントに特に便利です。

# フィールド

```
- glyph_id::Culong 関連するフォント内のcharを表すグリフのID。
- font::FTFont この文字を表示するために使用されるフォント。
- font_family::FontFamily 文字のフォントファミリー。
- slanted::Bool このcharがイタリック体と見なされるかどうか。
- represented_char::Char このcharによって表されるchar。
    場合によってはcharとは異なる。
```
