```
label_number(;precision=2, scale=1, prefix="", suffix="", decimal_mark=".", comma_mark=",", style_positive=:none, style_negative=:hyphen, kwargs...)
```

数値をさまざまなスタイリングオプションで文字列としてフォーマットします。

# 引数

  * `precision`: 小数点以下の桁数。
  * `scale`: フォーマット前に数値に適用されるスケーリングファクター。
  * `prefix`: 数値の前に追加する文字列。
  * `suffix`: 数値の後に追加する文字列。
  * `decimal_mark`: 小数点として使用する文字。
  * `comma_mark`: 千の区切りとして使用する文字。
  * `style_positive`: 正の数のスタイル (:none, :plus, :space)。
  * `style_negative`: 負の数のスタイル (:hyphen, :parens)。
  * `kwargs`: `Format.jl` の `format` に渡される追加のキーワード引数。

# 例

```julia
labeler = label_number(precision=0, suffix="kg")
labeler([1500.12, -2000.12]) # ["1,500kg", "-2,000kg"]
```
