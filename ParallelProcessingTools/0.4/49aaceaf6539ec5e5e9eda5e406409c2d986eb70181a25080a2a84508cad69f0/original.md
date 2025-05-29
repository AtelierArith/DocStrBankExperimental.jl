```
struct AutoThreadPinning
```

ParallelProcessingTools default thread pinning mode.

Constructor:

```julia
AutoThreadPinning(; random::Bool = false, pin_blas::Bool = false)
```

Arguments:

  * `random`: Use system topology based random thread pinning if no thread         affinity mask is set (e.g. via SLURM, `taskset`).
  * `blas`: Try to pin BLAS threads. Not fully functional due to bugs in BLAS thread pinning (see ThreadPinning issue [#105](https://github.com/carstenbauer/ThreadPinning.jl/issues/105)).

Use with `ThreadPinning.pinthreads`:

```julia
using ParallelProcessingTools, ThreadPinning
pinthreads(AutoThreadPinning())
```
