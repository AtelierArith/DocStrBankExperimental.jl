# `PlutoReport`

A Package to make reports and talks in [Pluto.jl](https://github.com/fonsp/Pluto.jl).

## Usage

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
