```
colorscheme_to_text(cscheme::ColorScheme, schemename, filename;
    category="オランダの画家",   # category
    notes="本当に失われているわけではない" # notes
)
```

ColorSchemeをJuliaのテキストファイルに書き込みます。

## 例

```
colorscheme_to_text(ColorSchemes.vermeer,
    "the_lost_vermeer",          # name
    "/tmp/the_lost_vermeer.jl",  # file
    category="オランダの画家",   # category
    notes="本当に失われているわけではない" # notes
    )
```

そして、次のように読み戻します：

```
include("/tmp/the_lost_vermeer.jl")
```
