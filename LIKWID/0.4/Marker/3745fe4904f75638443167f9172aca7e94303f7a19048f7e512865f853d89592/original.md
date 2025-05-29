```
perfmon_marker(f, group_or_groups[; kwargs...])
```

Monitor performance groups in marked areas (see [`@marker`](@ref)) while executing the given function `f` on one or multiple Julia threads.

**This is an experimental feature!**

Note that

  * `Marker.init_dynamic`, `Marker.init`, `Marker.close`, and `PerfMon.finalize` are called automatically
  * the measurement of multiple performance groups is sequential and requires multiple executions of `f`!

**Keyword arguments:**

  * `cpuids` (default: currently used CPU threads): specify the CPU threads (~ cores) to be monitored
  * `autopin` (default: `true`): automatically pin Julia threads to the CPU threads (~ cores) they are currently running on (to avoid migration and wrong results).
  * `keep` (default: `false`): keep the temporarily created marker file

# Example

```julia
julia> using LIKWID

julia> perfmon_marker("FLOPS_DP") do
           # only the marked regions are monitored!
           NUM_FLOPS = 100_000_000
           a = 1.8
           b = 3.2
           c = 1.3
           @marker "calc_flops" for _ in 1:NUM_FLOPS
                c = a * b + c
            end
           z = a*b+c
           @marker "exponential" exp(z)
           sin(c)
       end

Region: calc_flops, Group: FLOPS_DP
┌───────────────────────────┬───────────┐
│                     Event │  Thread 1 │
├───────────────────────────┼───────────┤
│          ACTUAL_CPU_CLOCK │ 3.00577e8 │
│             MAX_CPU_CLOCK │ 2.08917e8 │
│      RETIRED_INSTRUCTIONS │ 3.00005e8 │
│       CPU_CLOCKS_UNHALTED │ 3.00067e8 │
│ RETIRED_SSE_AVX_FLOPS_ALL │     1.0e8 │
│                     MERGE │       0.0 │
└───────────────────────────┴───────────┘
┌──────────────────────┬───────────┐
│               Metric │  Thread 1 │
├──────────────────────┼───────────┤
│  Runtime (RDTSC) [s] │ 0.0852431 │
│ Runtime unhalted [s] │  0.122687 │
│          Clock [MHz] │   3524.84 │
│                  CPI │   1.00021 │
│         DP [MFLOP/s] │   1173.12 │
└──────────────────────┴───────────┘

Region: exponential, Group: FLOPS_DP
┌───────────────────────────┬──────────┐
│                     Event │ Thread 1 │
├───────────────────────────┼──────────┤
│          ACTUAL_CPU_CLOCK │  85696.0 │
│             MAX_CPU_CLOCK │  59192.0 │
│      RETIRED_INSTRUCTIONS │   5072.0 │
│       CPU_CLOCKS_UNHALTED │   6013.0 │
│ RETIRED_SSE_AVX_FLOPS_ALL │     27.0 │
│                     MERGE │      0.0 │
└───────────────────────────┴──────────┘
┌──────────────────────┬────────────┐
│               Metric │   Thread 1 │
├──────────────────────┼────────────┤
│  Runtime (RDTSC) [s] │ 2.60005e-7 │
│ Runtime unhalted [s] │ 3.49786e-5 │
│          Clock [MHz] │    3546.95 │
│                  CPI │    1.18553 │
│         DP [MFLOP/s] │    103.844 │
└──────────────────────┴────────────┘

```
