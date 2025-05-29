```
gif_decode(filepath::AbstractString; use_localpalette=false)
```

GIF画像を色成分行列としてデコードします。ソースデータはファイル名である必要があります。

#### 引数

  * `filepath::AbstractString` : gifファイルへのパス
  * `use_localpalette::Bool=false` : デコード中に、この引数を使用することで特定のスライスに対してローカルカラーマップまたはグローバルカラーマップの使用を指定できます。Gifファイルはパレットベースであり、グローバルカラーマップ（最大`256色`）を持っていますが、gif内のスライス/画像は特定のスライス/画像に固有のローカルカラーマップを持つことができます。

#### 例

```jl julia> using GIFImages, Downloads

julia> path = "test/data/fire.gif" "test/data/fire.gif"

julia> img = gif_decode(path) 60×30×33 Array{RGB{N0f8},3} with eltype RGB{N0f8}
```
