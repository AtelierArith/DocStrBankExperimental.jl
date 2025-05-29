```
heatmap(values::AbstractArray, words)
```

単語のヒートマップを作成します。各単語の背景色は、その対応する値によって決まります。引数 `values` と `words`（およびオプションで `colors`）は同じサイズでなければなりません。

## キーワード引数

  * `colorscheme::Union{ColorScheme,Symbol}`: ColorSchemes.jl からのカラースキーム。デフォルトは `ColorSchemes.seismic` です。
  * `rangescale::Symbol`: カラーチャンネルが減少したヒートマップがカラースキームが適用される前にどのように正規化されるかを選択します。`：extrema` または `：centered` のいずれかでなければなりません。デフォルトは、デフォルトのカラースキーム `seismic` と一緒に使用するために `：centered` です。
