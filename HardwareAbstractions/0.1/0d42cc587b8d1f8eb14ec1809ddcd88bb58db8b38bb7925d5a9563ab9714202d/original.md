```
Csf = SysFilter(sys_discrete::StateSpace)
Csf = SysFilter(sys_continuous::StateSpace, sampletime)
Csf = SysFilter(sys::StateSpace, state::AbstractVector)
```

Returns an object used for filtering signals through LTI systems. Create a SysFilter object that can be used to implement control loops and simulators with LTI systems, i.e., `U(z) = C(z)E(z)`. To filter a signal `u` through the filter, call like `y = Csf(u)`. Calculates the filtered output `y` in `y = Cx+Du, x'=Ax+Bu`
