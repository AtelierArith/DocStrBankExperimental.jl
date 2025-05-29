```
perfmon(f, group_or_groups[; cpuids, autopin=true]) -> metrics, events
```

Monitor performance groups while executing the given function `f` on one or multiple Julia threads. Note that

  * `PerfMon.init` and `PerfMon.finalize` are called automatically
  * the measurement of multiple performance groups is sequential and requires multiple executions of `f`!

The returned data structures `metrics` and `events` are nested and different levels correspond to performance groups, threads, and measured metrics (in this order).

**Keyword arguments:**

  * `cpuids` (default: currently used CPU threads): specify the CPU threads (~ cores) to be monitored
  * `autopin` (default: `true`): automatically pin Julia threads to the CPU threads (~ cores) they are currently running on (to avoid migration and wrong results).
  * `print` (default: `true`): toggle printing of result tables
  * `finalize` (default: `true`): call `PerfMon.finalize` in the end

# Example

```julia
julia> using LIKWID

julia> x = rand(1000); y = rand(1000);

julia> metrics, events = perfmon("FLOPS_DP") do
           x .+ y;
       end;

Group: FLOPS_DP
┌───────────────────────────┬───────────┐
│                     Event │  Thread 1 │
├───────────────────────────┼───────────┤
│          ACTUAL_CPU_CLOCK │ 2.32582e8 │
│             MAX_CPU_CLOCK │ 1.61685e8 │
│      RETIRED_INSTRUCTIONS │ 3.12775e8 │
│       CPU_CLOCKS_UNHALTED │ 2.29064e8 │
│ RETIRED_SSE_AVX_FLOPS_ALL │    4964.0 │
│                     MERGE │       0.0 │
└───────────────────────────┴───────────┘
┌──────────────────────┬───────────┐
│               Metric │  Thread 1 │
├──────────────────────┼───────────┤
│  Runtime (RDTSC) [s] │ 0.0659737 │
│ Runtime unhalted [s] │ 0.0949394 │
│          Clock [MHz] │   3524.02 │
│                  CPI │  0.732361 │
│         DP [MFLOP/s] │ 0.0752421 │
└──────────────────────┴───────────┘

julia> first(metrics["FLOPS_DP"]) # all metrics of the first Julia thread
OrderedDict{String, Float64} with 5 entries:
  "Runtime (RDTSC) [s]"  => 0.0659737
  "Runtime unhalted [s]" => 0.0949394
  "Clock [MHz]"          => 3524.02
  "CPI"                  => 0.732361
  "DP [MFLOP/s]"         => 0.0752421

julia> first(events["FLOPS_DP"]) # all raw events of the first Julia thread
OrderedDict{String, Float64} with 6 entries:
  "ACTUAL_CPU_CLOCK"          => 2.32582e8
  "MAX_CPU_CLOCK"             => 1.61685e8
  "RETIRED_INSTRUCTIONS"      => 3.12775e8
  "CPU_CLOCKS_UNHALTED"       => 2.29064e8
  "RETIRED_SSE_AVX_FLOPS_ALL" => 4964.0
  "MERGE"                     => 0.0

julia> metrics, events = perfmon(("FLOPS_DP", "MEM1")) do
           x .+ y;
       end;

Group: FLOPS_DP
┌───────────────────────────┬──────────┐
│                     Event │ Thread 1 │
├───────────────────────────┼──────────┤
│          ACTUAL_CPU_CLOCK │  85773.0 │
│             MAX_CPU_CLOCK │  60074.0 │
│      RETIRED_INSTRUCTIONS │   6605.0 │
│       CPU_CLOCKS_UNHALTED │  32291.0 │
│ RETIRED_SSE_AVX_FLOPS_ALL │   1000.0 │
│                     MERGE │      0.0 │
└───────────────────────────┴──────────┘
┌──────────────────────┬────────────┐
│               Metric │   Thread 1 │
├──────────────────────┼────────────┤
│  Runtime (RDTSC) [s] │ 9.99103e-6 │
│ Runtime unhalted [s] │ 3.50123e-5 │
│          Clock [MHz] │    3497.79 │
│                  CPI │    4.88887 │
│         DP [MFLOP/s] │     100.09 │
└──────────────────────┴────────────┘

Group: MEM1
┌──────────────────────┬──────────┐
│                Event │ Thread 1 │
├──────────────────────┼──────────┤
│     ACTUAL_CPU_CLOCK │ 185118.0 │
│        MAX_CPU_CLOCK │ 129042.0 │
│ RETIRED_INSTRUCTIONS │   6213.0 │
│  CPU_CLOCKS_UNHALTED │  15122.0 │
│       DRAM_CHANNEL_0 │    148.0 │
│       DRAM_CHANNEL_1 │    110.0 │
│       DRAM_CHANNEL_2 │    319.0 │
│       DRAM_CHANNEL_3 │    326.0 │
└──────────────────────┴──────────┘
┌────────────────────────────────────────────┬────────────┐
│                                     Metric │   Thread 1 │
├────────────────────────────────────────────┼────────────┤
│                        Runtime (RDTSC) [s] │ 6.53034e-6 │
│                       Runtime unhalted [s] │ 7.55646e-5 │
│                                Clock [MHz] │    3514.37 │
│                                        CPI │    2.43393 │
│ Memory bandwidth (channels 0-3) [MBytes/s] │    8849.77 │
│ Memory data volume (channels 0-3) [GBytes] │  5.7792e-5 │
└────────────────────────────────────────────┴────────────┘

```
