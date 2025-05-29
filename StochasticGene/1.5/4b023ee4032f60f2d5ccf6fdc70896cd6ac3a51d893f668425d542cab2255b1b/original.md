```
write_traces_coupling_spawn(folder, datapath, datacond, interval, G=(3, 3), R=(3, 3),
                           sources=1:3, targets=1:5, ratetype::String="median",
                           start=1, stop=-1, probfn=prob_Gaussian, noiseparams=4,
                           splicetype=""; hlabel="-h", state=true, pattern="gene")
```

Parallelized version of write*traces*coupling using Julia's task-based parallelism with @spawn. This provides more dynamic scheduling which can be beneficial for workloads with varying execution times.
