```
GhostSkeleton(cut::EmbeddedDiscretization[,in_or_out=ACTIVE_IN])
```

Creates a triangulation containing the ghost facets. Ghosts facets are defined as the facets  of the **background mesh** that are adjacent to at least one `CUT` background cell.

Mostly used for CUT-FEM stabilisation. 
