```
GroupedCoefplot
```

`GroupedCoefplot`オブジェクト。これは、グループ化されたコエフプロットを描画するためのすべての情報を含んでいます。コンストラクタのキーワード引数はすべてオプションです。

# コンストラクタ

```julia
GroupedCoefplot(data::Pair{<:Any, Coefplot}...;  <keyword arguments>)
GroupedCoefplot(gdata::GroupedDataFrame;  <keyword arguments>)
```

# 引数

  * `title::Label`: プロットのタイトル。
  * `xlabel::Label`: プロットのx軸ラベル。
  * `ylabel::Label`: プロットのy軸ラベル。
  * `xticklabel::CaptionStyle`: x軸の目盛りのスタイル。
  * `yticklabel::CaptionStyle`: y軸の目盛りのスタイル。
  * `width::Real = 240`: 軸フレームの幅。
  * `height::Real = 204`: 軸フレームの高さ。
  * `note::Union{Note, Missing}`: プロットの南側に添付されるノート。
  * `vertical::Bool = true`: `true`の場合、エラーバーはy軸に平行です; `false`の場合、エラーバーはx軸に平行です。
