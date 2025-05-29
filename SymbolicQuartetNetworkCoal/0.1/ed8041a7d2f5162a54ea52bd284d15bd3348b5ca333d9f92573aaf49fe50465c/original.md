```
makeEdgeLabel(net; showTerminalEdgeLabels=false)
```

Generates a dataframe mapping edge numbers to their symbolic labels.

## Description

This function creates labels for the edges of a `HybridNetwork` in the format `"t_{e}"`, where `e` is the edge number.   By default, labels are only assigned to **non-terminal edges** (i.e., edges that do not end at leaf nodes).   The output dataframe is used as input for PhyloPlots' option `edgelabel=``. Setting`showTerminalEdgeLabels=true` includes labels for terminal edges as well.

## Arguments

  * `net`: A `HybridNetwork` object.
  * `showTerminalEdgeLabels`: A boolean flag (default = `false`).  

      * `false`: Excludes terminal edges.
      * `true`: Includes all edges.

## Returns

  * A `DataFrame` with columns:

      * `number`: Edge numbers.
      * `label`: Corresponding symbolic labels (`"t_{e}"`).
