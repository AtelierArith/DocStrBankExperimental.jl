`SourceData(mod::Module, row::DataFrameRow)` applies create an `SourceData` objects from a row of a `DataFrame` (i.e., `dataset_table(mod)`), with `abspath!` applied.

This is for loading data according to `dataset_table`; thus, paths should be referred to that in mod instead of being relative to the current directory.
