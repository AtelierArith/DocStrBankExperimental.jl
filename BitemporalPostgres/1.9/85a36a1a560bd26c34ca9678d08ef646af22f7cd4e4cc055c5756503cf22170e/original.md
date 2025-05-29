mkforest(hid::DbId)::Vector{Node}

```
builds a forest of version nodes where
* eventual child node vectors denote mutations which have been retrospectively corrected by their predecessor


see: Theory: Textual representation of mutation histories
```
