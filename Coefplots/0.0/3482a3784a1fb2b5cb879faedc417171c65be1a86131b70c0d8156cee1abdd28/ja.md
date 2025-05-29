```
GroupedMultiCoefplot
```

`GroupedMultiCoefplot`オブジェクト。これは、複数の`GroupedCoefplot`を一緒にプロットするためのすべての情報を含んでいます。コンストラクタのキーワード引数はすべてオプションです。

# コンストラクタ

```julia
GroupedMultiCoefplot(data::Pair{<:Any, GroupedCoefplot} ...;  <keyword arguments>)
GroupedMultiCoefplot(data::Pair{<:Any, MultiCoefplot} ...;  <keyword arguments>)
```

# 引数

  * `title::Label`: プロットのタイトル。
  * `xlabel::Label`: プロットのx軸ラベル。
  * `ylabel::Label`: プロットのy軸ラベル。
  * `xticklabel::CaptionStyle`: x軸の目盛りのスタイル。
  * `yticklabel::CaptionStyle`: y軸の目盛りのスタイル。
  * `show_legend::Union{Vector{Bool}, Missing} = missing`: サブプロットのどの凡例を表示するかを指定するブールベクトル。デフォルトは最初の凡例のみを表示します。
  * `width::Real = 240`: 軸フレームの幅。
  * `height::Real = 204`: 軸フレームの高さ。
  * `interval::Union{Real,Missing} = missing`: 各`Coefplot`間の距離を決定します。各`Coefplot`の`offset`はこれに基づいて計算されます。
  * `note::Union{Note, Missing}`: プロットの南側に添付されるノート。
  * `vertical::Bool = true`: `true`の場合、エラーバーはy軸に平行です。`false`の場合、エラーバーはx軸に平行です。
