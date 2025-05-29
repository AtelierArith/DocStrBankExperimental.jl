```
m = pcsaft_m_from_acentric(w)
```

Given the acentric factor of a component, returns the segment length that corresponds to the real acentric factor calculated by the PCSAFT equation of state.

Inputs:

  * `ω` : acentric factor (no units)

Outputs:

  * `m`: Segment length (no units).  Returns `NaN` if the value is outside the range of the ancillary (0.005073686089814064 ≤ w ≤ 6.0465684112508296).
