テーマに対する「スタイルシート」を生成します。

```julia
stylesheet(io, mime)
stylesheet(io, mime, theme)

```

指定された `theme` でソースコードを色付けするために必要なスタイル情報を出力します。`theme` はデフォルトで `Themes.DefaultTheme` になります。出力は `mime` の形式で `io` に印刷されます。`mime` は次のいずれかです。

  * `MIME("text/html")`
  * `MIME("text/css")`
  * `MIME("text/latex")`

# 例

```jldoctest
julia> using Highlights

julia> buf = IOBuffer();

julia> stylesheet(buf, MIME("text/css"), Themes.EmacsTheme)

```
