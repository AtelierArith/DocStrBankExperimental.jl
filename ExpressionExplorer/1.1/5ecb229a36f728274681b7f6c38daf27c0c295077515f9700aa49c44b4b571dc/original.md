Turn a `SymbolsState` into a `ReactiveNode`. The main differences are:

  * A `SymbolsState` is a nested structure of function definitions inside function definitions inside... This conversion flattens this structure by merging `SymbolsState`s from defined functions.
  * `ReactiveNode` functions as a cache to improve efficiently, by turning the nested structures into multiple `Set{Symbol}`s with fast lookups.
