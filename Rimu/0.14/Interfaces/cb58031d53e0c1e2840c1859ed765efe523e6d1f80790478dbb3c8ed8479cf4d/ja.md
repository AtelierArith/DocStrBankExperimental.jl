```
sort_into_targets!(target, source, stats) -> target, source, agg_stats
```

`source` から `target` へ、そして `stats` から `agg_stats` へ、スレッドまたは MPI レベルの並列性に従って係数を集約します。

新しい `target` と `source` を返します。ソートプロセスでは、それらを入れ替えることがあるためです。
