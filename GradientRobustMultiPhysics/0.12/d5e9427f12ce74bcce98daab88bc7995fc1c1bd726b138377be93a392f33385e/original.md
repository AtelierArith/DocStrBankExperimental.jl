```
function evaluate!(
    result,                     # target for result
    PE::PointEvaluator,         
    xref,                       # local coordinates inside item
    item                        # item number
    ) where  {T, Tv, Ti, FEType, FEOP, AT, ACT}
```

Evaluates the PointEvaluator at the point with the given local coordinates insides the item with the specified item number. (To get the local coordinates, currently a CellFinder has to be maintained manually, this might change in future.)
