```
MultiCoefplot
```

`MultiCoefplot`オブジェクト。これは、複数の`Coefplot`を一緒にプロットするためのすべての情報を含んでいます。コンストラクタのキーワード引数はすべてオプションです。

# コンストラクタ

```julia
MultiCoefplot(data::Coefplot ...; <keyword arguments>)
```

# 引数

  * `title::Label`: プロットのタイトル。
  * `xlabel::Label`: プロットのx軸ラベル。
  * `ylabel::Label`: プロットのy軸ラベル。
  * `xticklabel::CaptionStyle`: x軸の目盛りのスタイル。
  * `yticklabel::CaptionStyle`: y軸の目盛りのスタイル。
  * `legend::Legend`: 凡例のスタイル。
  * `width::Real = 240`: 軸フレームの幅。
  * `height::Real = 204`: 軸フレームの高さ。
  * `interval::Union{Real,Missing} = missing`: 各`Coefplot`間の距離を決定します。各`Coefplot`の`offset`はこれに基づいて計算されます。
  * `sorter::Vector{String} = String[]`: 係数の内容と順序を示すベクトル。空の場合は、各Coefplotのdata.varnameの和集合を使用します。
  * `csorter::Vector{String} = String[]`: coefplotsの順序を示すベクトル。空の場合は、データの順序を使用します。
  * `note::Union{Note, Missing}`: プロットの南側に添付されるノート。
  * `vertical::Bool = true`: `true`の場合、エラーバーはy軸に平行; `false`の場合、エラーバーはx軸に平行です。

以下の引数は`Coefplots()`からのもので、`MultiCoefplot()`で指定された場合は各`Coefplot`に渡されます。

  * `keepmark::Bool = true`: ユーザーが点推定をプロットしたい場合は`true`、そうでない場合は`false`。
  * `keepconnect::Bool = false`: ユーザーが隣接する点推定を接続したい場合は`true`、そうでない場合は`false`。
  * `mark::Mark`: 点推定のマークのスタイル。
  * `errormark:Mark`: 信頼区間の端点のマークのスタイル。
  * `errorbar::Bar`: エラーバーのスタイル。
  * `connect::Bar`: 隣接する点推定を接続する線のスタイル。
  * `offset::Real = 0`: Stataパッケージのものに似ており、係数名を表す軸に沿ってcoefplotをシフトします。
  * `sorter::Vector{String} = String[]`: 係数の内容と順序を示すベクトル。空の場合は、data.varnameの順序を使用します。
  * `level::Real = 0.95`: 信頼レベル。
