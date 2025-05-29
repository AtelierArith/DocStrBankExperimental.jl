```
    PDPageTextRun
```

In PDF text may not be contiguous as there may be chnge of font, style, graphics rendering parameters. `PDPageTextRun` is a unit of text which can be rendered without any change to the graphical parameters. There is no guarantee that a text run will represent a meaningful word or sentence.

`PDPageTextRun` is a composition implementation of [`PDPageElement`](@ref).
