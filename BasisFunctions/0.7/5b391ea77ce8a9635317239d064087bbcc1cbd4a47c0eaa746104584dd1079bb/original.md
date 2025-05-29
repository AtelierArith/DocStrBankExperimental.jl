A partition divides a region into several subregions. The main algorithm of every partition is deciding in which subregion a given point x lies, implemented by the `partition_index` function.

The intent of a partition is to be combined with a function set on each subregion, effectively creating a piecewise function.

The pieces of a partition have an index ranging from 1 to length(partition).
