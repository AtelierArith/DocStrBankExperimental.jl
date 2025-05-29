```julia
get_code_unsafe(modulation, system, phase, prn)

```

Get code of LOC at phase `phase` of PRN `prn`. The phase will not be wrapped by the code length. The phase has to be smaller than the code length incl. secondary code.
