# `PlutoReport`

[Pluto.jl](https://github.com/fonsp/Pluto.jl)を使ってレポートや講演を作成するためのパッケージです。

## 使用法

```
using PlutoReport

@bind pval presentation_controls(aside=true)

presentation_ui(pval)

apply_css_fixes()

Title("A test title", "some subtitle", "Some person", "Some institution")

md"## A beautiful Report"

@bind references References()

display_bibliography("./bibliography.bibtex", references)
```
