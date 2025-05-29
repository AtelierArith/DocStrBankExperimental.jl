```
freeze(cr::CommonRandomRecorder)::FrozenCommonRandomRecorder
```

The [CommonRandomRecorder](@ref) records every time it sees a clock request random number generation. It continues to do that every time it runs, which is a problem if you run simulations for comparison on multiple threads. If you want to use CRN and to use multiple threads for subsequent simulation runs, then first run the simulation a bunch of times on one thread. Then freeze the simulation, and then the frozen version will stop remembering new threads.

There is one part of the frozen recorder that will be mutable because it's useful for debugging, the record of missed clocks. Freeze a recorder for each thread, and each thread will track its own misses. They will all work from the same copy of the recorded random number generator states.
