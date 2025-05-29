`SourceData(mod::Module, row::DataFrameRow)` は、`DataFrame` の行（すなわち、`dataset_table(mod)`）から `SourceData` オブジェクトを作成します。この際、`abspath!` が適用されます。

これは `dataset_table` に従ってデータをロードするためのものであり、そのため、パスは現在のディレクトリに対して相対的ではなく、mod内で参照されるべきです。
