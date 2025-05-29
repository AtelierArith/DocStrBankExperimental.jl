`DMPopts(Nbasis,αx,αz) = DMPopts(Nbasis, αx, αz, βz = αz/4)`

Holds parameters for fitting a DMP

# Fields

`Nbasis,αx,αz,βz,sched_sig,fitmethod`

`sched_sig` can be chosen as `:canonical` (default), `:time` or `position`

`fitmethod` can be chosen as `:lwr` or `:leastsquares`

See example file or the paper by Ijspeert et al. 2013
