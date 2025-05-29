```
PGF([output::Union{IO,AbstractString}], width=√200cm, height=10cm, only_tikz=false; texfonts=false) -> Backend
```

ポータブルグラフィックスフォーマットバックエンドを作成します。出力は通常[`draw`](@ref)に渡されます。最初の引数として文字列を使用してファイル名を指定します。`only_tikz`がtrueの場合、出力は「tikzpicture」ですが、そうでない場合はヘッダーとフッターを含む完全なlatexドキュメントになります。`texfonts`がfalseの場合、ヘッダーに「\usepackage{fontspec}」を含めます。

# 例

```
c = compose(context(), rectangle())
draw(PGF("myplot.tex", 10cm, 5cm, only_tikz=true, texfonts=true), c)
```
