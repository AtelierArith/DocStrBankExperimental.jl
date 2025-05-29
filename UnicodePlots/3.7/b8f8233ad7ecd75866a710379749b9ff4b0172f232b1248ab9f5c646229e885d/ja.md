```
savefig(p, filename; color = false, kw...)
```

与えられたプロットを `txt` または `png` ファイルに保存します。

# 引数 - `txt`

  * `color::Bool = false`: ANSI カラーコードをファイルに出力します。

# 引数 - `png`

ヘルプを参照してください: `? UnicodePlots.png_image`

# 例

```julia-repl
julia> savefig(lineplot([0, 1]), "foo.txt")
julia> savefig(lineplot([0, 1]), "foo.png"; font = "JuliaMono", pixelsize = 32, transparent = false)
```
