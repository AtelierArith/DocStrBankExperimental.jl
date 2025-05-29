```julia
read_optimizer_stats(
    res::PowerSimulations.SimulationProblemResults;
    store
) -> Any

```

問題の最適化統計をDataFrameとして返します。

# 受け入れられるキーワード

  * `store::SimulationStore`: 読み取りのために開かれたストア
