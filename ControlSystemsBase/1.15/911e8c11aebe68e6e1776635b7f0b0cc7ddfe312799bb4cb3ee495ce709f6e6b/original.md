```
wgm, gm, wpm, pm = margin(sys::LTISystem, w::Vector; full=false, allMargins=false, adjust_phase_start=true)
```

returns frequencies for gain margins, gain margins, frequencies for phase margins, phase margins

  * If `!allMargins`, return only the smallest margin
  * If `full` return also `fullPhase`
  * `adjust_phase_start`: If true, the phase will be adjusted so that it starts at -90*intexcess degrees, where `intexcess` is the integrator excess of the system.

See also [`delaymargin`](@ref) and [`RobustAndOptimalControl.diskmargin`](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/api/#RobustAndOptimalControl.diskmargin)
