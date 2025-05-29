Wildcards are used to match multiple keys or indices in a JSON path at once. There are four types of wildcards:

  * `ANY_KEY` - Matches any key in a `Dict`.
  * `ANY_INDEX` - Matches any index in a `Vector`.
  * `ANY` - Matches any key or in a `Dict` or index in a `Vector`.
  * `SKIP_LIST` - If current value in the path is a `Vector`, matches all indices. If the current value is not a `Vector` it has no effect except for packing current value into a result Tuple with one element.

The wildcards can only be used for reading data, not for setting it.
