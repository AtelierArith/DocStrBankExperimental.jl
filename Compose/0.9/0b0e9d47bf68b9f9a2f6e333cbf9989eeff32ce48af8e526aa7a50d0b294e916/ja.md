```
PS([output::Union{AbstractString, IO}], width=√200cm, height=10cm; dpi=72) -> Backend
```

Postscriptバックエンドを作成します。出力は通常[`draw`](@ref)に渡されます。最初の引数として文字列を使用してファイル名を指定します。`Cairo.jl`に依存しています。

# 例

```
using Cairo
c = compose(context(), circle())
draw(PS("myplot.ps", 10cm, 5cm, dpi=250), c)
```
