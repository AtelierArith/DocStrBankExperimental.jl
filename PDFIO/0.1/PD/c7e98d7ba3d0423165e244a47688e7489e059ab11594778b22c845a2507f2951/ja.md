```
    pdPageGetFonts(page::PDPage) -> Dict{CosName, PDFont}()
```

ページ内のフォントの辞書を返します。

#例

```
julia> pdPageGetFonts(page)
Dict{CosName,PDFIO.PD.PDFont} with 4 entries:
  /F0 => PDFont(…
  /F4 => PDFont(…
  /F8 => PDFont(…
  /F9 => PDFont(…

```
