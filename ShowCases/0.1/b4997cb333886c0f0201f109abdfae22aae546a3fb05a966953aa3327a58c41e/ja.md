```
ShowProps(o, props=propertynames(o);
          show_keywords=true, new_lines=false, keyword_style=Style(), entry_style=Style()
          separator=(new_lines ? Print(" = ") : Print("=")),
          kw...)
```

オブジェクト `o` のプロパティを [`ShowList`](@ref) を介して表示し、エントリには `ShowKw` を使用します。

## 引数

  * `props`: 表示するプロパティの名前を持つシンボル。
  * `show_keywords`: プロパティ名を表示するかどうか。
  * `keyword_style::Style`: キーワードに適用するスタイル。
  * `entry_style::Style`: エントリに適用するスタイル。
  * `separator`: キーワードとプロパティの間に使用するセパレーター。デフォルトでは、`new_lines` が true の場合にスペースが追加されます。
  * `kw`: [`ShowList`](@ref) に渡される他のキーワード。

## 例

```
julia> propertynames(1.0 + im)
(:re, :im)

julia> ShowProps(1.0 + im)
(re=1.0, im=1.0)

julia> ShowProps(1.0 + im, [:re])
(re=1.0)

julia> ShowProps(1.0 + im, [:re], keyword_style=Style(:red), new_lines=true)
(
    re = 1.0
)

julia> ShowProps(1.0 + im, show_keywords=false)
(1.0, 1.0)
```
