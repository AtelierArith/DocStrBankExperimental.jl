```
plot(X, Ys::AbstractVector{<:Union{AbstractVector, Tuple}}; xlabel="", ylabel="",
labels=nothing, xlims=nothing, ylims=nothing, ann=nothing, scatter=false, 
title="", fig="", ysize=14, disp=false)
```

共通のx軸`X`に対して`Ys`で与えられた複数の曲線をプロットします。

# 引数

  * `X`: x軸の値。
  * `Ys`: 各曲線のy軸の値を表すベクトルのベクトル。

# オプション引数

  * `xlabel`: x軸のラベル。デフォルトは空の文字列です。
  * `ylabel`: y軸のラベル。デフォルトは空の文字列です。
  * `labels`: 各曲線のラベル。デフォルトは`nothing`です。
  * `xlims`: x軸の制限。デフォルトは`nothing`です。
  * `ylims`: y軸の制限。デフォルトは`nothing`です。
  * `ann`: プロットに配置される注釈。デフォルトは`nothing`です。
  * `scatter`: 点を散布図としてプロットするかどうかを示すブール値。デフォルトは`false`です。
  * `title`: 図のタイトル。デフォルトは空の文字列です。
  * `fig`: 図の名前。デフォルトは空の文字列です。
  * `ysize`: y軸ラベルのフォントサイズ。デフォルトは14です。
  * `disp`: プロットを表示するかどうかを示すブール値。falseの場合、後で表示するための構造体のみを作成します。デフォルトは`false`です。
