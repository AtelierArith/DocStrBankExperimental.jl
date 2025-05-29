```
    pdPageGetFonts(page::PDPage) -> Dict{CosName, PDFont}()
```

Returns a dictionary of fonts in the page.

#Example

```
julia> pdPageGetFonts(page)
Dict{CosName,PDFIO.PD.PDFont} with 4 entries:
  /F0 => PDFont(…
  /F4 => PDFont(…
  /F8 => PDFont(…
  /F9 => PDFont(…

```
