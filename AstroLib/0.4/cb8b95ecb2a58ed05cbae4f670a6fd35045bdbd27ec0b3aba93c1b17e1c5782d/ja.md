```
ordinal(num) -> result
```

### 目的

整数を正しい英語の序数文字列に変換します。

### 説明

最初の4つの序数文字列は「1st」、「2nd」、「3rd」、「4th」、....

### 引数

  * `num`: 序数にする数値。型は `Integer` である必要があります。

### 出力

  * `result`: 序数文字列、例えば「1st」、「3rd」、「164th」、「87th」など。

### 例

```jldoctest
julia> using AstroLib

julia> ordinal.(1:5)
5-element Vector{String}:
 "1st"
 "2nd"
 "3rd"
 "4th"
 "5th"
```

### 注意事項

この関数はIDLの実装とは異なり、浮動小数点引数をサポートしていません。この関数のコードはIDL Astronomy User's Libraryに基づいています。
