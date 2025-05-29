```
Coefplot
```

`Coefplot`オブジェクト。これは、coefplotをプロットするためのすべての情報を含んでいます。コンストラクタのキーワード引数はすべてオプションです。

# コンストラクタ

```julia
Coefplot(data::AbstractDataFrame; <keyword arguments>)
```

# 引数

  * `title::Label`: プロットのタイトル。
  * `xlabel::Label`: プロットのx軸ラベル。
  * `ylabel::Label`: プロットのy軸ラベル。
  * `xticklabel::CaptionStyle`: x軸の目盛りのスタイル。
  * `yticklabel::CaptionStyle`: y軸の目盛りのスタイル。
  * `width::Real = 240`: 軸フレームの幅。
  * `height::Real = 204`: 軸フレームの高さ。
  * `keepmark::Bool = true`: ユーザーが点推定をプロットしたい場合は`true`、そうでない場合は`false`。
  * `keepconnect::Bool = false`: ユーザーが隣接する点推定を接続したい場合は`true`、そうでない場合は`false`。
  * `mark::Mark`: 点推定のマークのスタイル。
  * `errormark:Mark`: 信頼区間の端点のマークのスタイル。
  * `errorbar::Bar`: エラーバーのスタイル。
  * `connect::Bar`: 隣接する点推定を接続する線のスタイル。
  * `offset::Real = 0`: Stataパッケージのものに似ており、係数名を表す軸に沿ってcoefplotをシフトします。
  * `sorter::Vector{String} = String[]`: 係数の内容と順序を示すベクター。空の場合は、`data.varname`の順序を使用します。
  * `level::Real = 0.95`: 信頼レベル。
  * `note::Union{Note, Missing}`: プロットの南に添付されるノート。
  * `vertical::Bool = true`: `true`の場合、エラーバーはy軸に平行です。`false`の場合、エラーバーはx軸に平行です。
