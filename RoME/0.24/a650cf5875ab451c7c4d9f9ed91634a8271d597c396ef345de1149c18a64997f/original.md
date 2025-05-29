```julia
getLastPoses(dfg; filterLabel, number)

```

Return the last `number::Int` of poses according to `filterLabel::Regex`.

Notes

  * Uses FIFO add history of variables to the distribued factor graph object as search index.

DevNotes

  * TODO consolidate with generic filter by regext on variable labels in IIF instead.
