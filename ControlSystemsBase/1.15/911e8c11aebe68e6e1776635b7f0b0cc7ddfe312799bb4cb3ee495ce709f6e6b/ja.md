```
wgm, gm, wpm, pm = margin(sys::LTISystem, w::Vector; full=false, allMargins=false, adjust_phase_start=true)
```

は、ゲインマージン、ゲインマージンの周波数、位相マージンの周波数、位相マージンを返します。

  * `!allMargins`の場合、最小のマージンのみを返します。
  * `full`の場合、`fullPhase`も返します。
  * `adjust_phase_start`: trueの場合、位相は-90*intexcess度から始まるように調整されます。ここで、`intexcess`はシステムのインテグレータの過剰です。

[`delaymargin`](@ref)および[`RobustAndOptimalControl.diskmargin`](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/api/#RobustAndOptimalControl.diskmargin)も参照してください。
