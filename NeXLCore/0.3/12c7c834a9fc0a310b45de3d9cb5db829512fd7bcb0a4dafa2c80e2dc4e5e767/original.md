```
loadcustommacs!(source::AbstractString, elms::AbstractArray{Element})
loadcustommacs!(source::AbstractString, elm::Element)
```

Load custom macs from the database associated with the specified source.

Sources include "Henke1974", "Henke1982", "Bastin1989", "Henke1993", "Bastin1997", "Ruste1979", "Kohlhaas1970", "Weisweiler1975",  "Bastin1990", "Bastin1988", "Poml2020", "Ruste1975", "Henke1982", "Farthing1990", "Sabbatucci2016"

Use `listcustommacs(cxr)` to explore available MACs.
