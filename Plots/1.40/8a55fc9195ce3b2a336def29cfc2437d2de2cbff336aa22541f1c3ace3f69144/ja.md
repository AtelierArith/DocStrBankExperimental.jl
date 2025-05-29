```
font(args...)
```

特徴のリストからフォントを作成します。値は引数（型/値によって区別される）またはキーワード引数として指定できます。

# 引数

  * `family`: AbstractString. "serif" または "sans-serif" または "monospace"
  * `pointsize`: Integer. フォントのサイズ（ポイント単位）
  * `halign`: Symbol. 水平揃え (:hcenter, :left, または :right)
  * `valign`: Symbol. 垂直揃え (:vcenter, :top, または :bottom)
  * `rotation`: Real. テキストの回転角度（度単位、非整数型を使用）
  * `color`: Colorant または Symbol

# 例

```julia-repl
julia> font(8)
julia> font(family="serif", halign=:center, rotation=45.0)
```
