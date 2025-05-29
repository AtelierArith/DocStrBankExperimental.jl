```
@perfmon_marker group_or_groups codeblock
```

**This is an experimental feature!**

See also: [`perfmon_marker`](@ref)

# Example

```julia
julia> using LIKWID

julia> @perfmon_marker "FLOPS_DP" begin
           @marker "exponential" exp(3.141)
       end

Region: exponential, Group: FLOPS_DP
┌───────────────────────────┬──────────┐
│                     Event │ Thread 1 │
├───────────────────────────┼──────────┤
│          ACTUAL_CPU_CLOCK │ 115146.0 │
│             MAX_CPU_CLOCK │  78547.0 │
│      RETIRED_INSTRUCTIONS │   4208.0 │
│       CPU_CLOCKS_UNHALTED │   7112.0 │
│ RETIRED_SSE_AVX_FLOPS_ALL │     10.0 │
│                     MERGE │      0.0 │
└───────────────────────────┴──────────┘
┌──────────────────────┬────────────┐
│               Metric │   Thread 1 │
├──────────────────────┼────────────┤
│  Runtime (RDTSC) [s] │ 3.02056e-8 │
│ Runtime unhalted [s] │ 4.70008e-5 │
│          Clock [MHz] │     3591.4 │
│                  CPI │    1.69011 │
│         DP [MFLOP/s] │    331.064 │
└──────────────────────┴────────────┘

```
