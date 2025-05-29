```
@perfmon group_or_groups codeblock
```

See also: [`perfmon`](@ref)

# Example

```
julia> using LIKWID

julia> x = rand(1000); y = rand(1000);

julia> metrics, events = @perfmon "FLOPS_DP" x .+ y;

Group: FLOPS_DP
┌───────────────────────────┬──────────┐
│                     Event │ Thread 1 │
├───────────────────────────┼──────────┤
│          ACTUAL_CPU_CLOCK │  88187.0 │
│             MAX_CPU_CLOCK │  61789.0 │
│      RETIRED_INSTRUCTIONS │   6705.0 │
│       CPU_CLOCKS_UNHALTED │  34181.0 │
│ RETIRED_SSE_AVX_FLOPS_ALL │   1000.0 │
│                     MERGE │      0.0 │
└───────────────────────────┴──────────┘
┌──────────────────────┬────────────┐
│               Metric │   Thread 1 │
├──────────────────────┼────────────┤
│  Runtime (RDTSC) [s] │ 1.08307e-5 │
│ Runtime unhalted [s] │ 3.59977e-5 │
│          Clock [MHz] │    3496.42 │
│                  CPI │    5.09784 │
│         DP [MFLOP/s] │    92.3302 │
└──────────────────────┴────────────┘

julia> first(metrics["FLOPS_DP"]) # all metrics of the first Julia thread
OrderedDict{String, Float64} with 5 entries:
  "Runtime (RDTSC) [s]"  => 8.56091e-6
  "Runtime unhalted [s]" => 3.22377e-5
  "Clock [MHz]"          => 3506.47
  "CPI"                  => 4.78484
  "DP [MFLOP/s]"         => 116.81

julia> first(events["FLOPS_DP"]) # all events of the first Julia thread
OrderedDict{String, Float64} with 6 entries:
  "ACTUAL_CPU_CLOCK"          => 78974.0
  "MAX_CPU_CLOCK"             => 55174.0
  "RETIRED_INSTRUCTIONS"      => 5977.0
  "CPU_CLOCKS_UNHALTED"       => 28599.0
  "RETIRED_SSE_AVX_FLOPS_ALL" => 1000.0
  "MERGE"                     => 0.0
```
