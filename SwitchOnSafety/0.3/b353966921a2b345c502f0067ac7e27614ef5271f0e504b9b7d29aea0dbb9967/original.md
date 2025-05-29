```
mdependentlift(s::AbstractDiscreteSwitchedSystem, m, forward=true)
```

Returns the `m`-path-dependent lift of the hybrid system `s` [LD06]. The corresponding automaton is the debruijn graph of dimension `m`. If `forward` is `false` then the debruijn graph works backward [ELD14].

[LD06] Lee, J.-W. & Dullerud, G. E. Uniform stabilization of discrete-time switched and Markovian jump linear systems Automatica, Elsevier, 2006, 42, 205-21

[ELD14] Essick, R. and Lee, J.-W. and Dullerud, G. E. Control of linear switched systems with receding horizon modal information IEEE Transactions on Automatic Control, 2014, 59, 2340-2352

[PEDJ16] Philippe, M. and Essick, R. and Dullerud, G. E. and Jungers, R. M. Stability of discrete-time switching systems with constrained switching sequences Automatica, 2016, 72, 242-250
