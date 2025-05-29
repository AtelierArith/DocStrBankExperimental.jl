```julia
sampleTF(
    tf::MPIFiles.TransferFunction,
    f::MPIFiles.MPIFile;
    numPeriodGrouping
) -> Any

```

測定 `f` によって定義された周波数で `tf` をサンプリングし、オプションで `numPeriodGrouping` を使用します。
