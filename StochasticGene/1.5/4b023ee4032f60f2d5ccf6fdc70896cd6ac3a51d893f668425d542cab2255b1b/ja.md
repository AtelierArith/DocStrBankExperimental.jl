```
write_traces_coupling_spawn(folder, datapath, datacond, interval, G=(3, 3), R=(3, 3),
                           sources=1:3, targets=1:5, ratetype::String="median",
                           start=1, stop=-1, probfn=prob_Gaussian, noiseparams=4,
                           splicetype=""; hlabel="-h", state=true, pattern="gene")
```

Juliaのタスクベースの並列処理を使用したwrite*traces*couplingの並列化バージョンで、@spawnを使用しています。これは、実行時間が異なるワークロードに対して有益な動的スケジューリングを提供します。
