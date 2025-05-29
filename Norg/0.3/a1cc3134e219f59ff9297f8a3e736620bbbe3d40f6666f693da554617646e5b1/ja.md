```
norg([codegentarget, ] s)
```

入力`s`をASTに解析します。codegentargetが含まれている場合は、指定されたターゲットのコード生成の結果を返します。

# 例

```julia-repl
julia> norg("* Hello world!")
NorgDocument
└─ (K"Heading1", 2, 8)
   └─ (K"ParagraphSegment", 4, 7)
      ├─ Hello
      ├─
      ├─ world
      └─ !
julia> norg(HTMLTarget(), "* Hello world!")
<div class="norg"><section id="section-h1-hello-world"><h1 id="h1-hello-world">Hello world&#33;</h1></section><section class="footnotes"><ol></ol></section></div>
```
