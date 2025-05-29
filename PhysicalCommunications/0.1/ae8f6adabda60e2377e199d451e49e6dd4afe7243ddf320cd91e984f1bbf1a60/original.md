```
buildeye(x::Vector, y::Vector, tbit::Number, teye::Number; tstart::Number=0)
```

Builds an eye diagram by folding `x` values of provided `(x,y)` into multiple windows of `teye` that start (are "triggered") every `tbit`.

Trace data is stored in a `DataEye` object as vectors of `(x,y)` sub-vectors.

Inputs:

  * tbit: Bit period (s).  Defines "trigger point" of each bit start.
  * teye: Eye period (s).  Defines how much of eye data (along x-axis) algorithm is to collect after "trigger point".  Typically, this is set to `2.0*tbit`.
  * tstart: Time of first "trigger point" (s).

Example plotting with Plots.jl:

```
#Assumption: (x, y) data generated here.
tbit = 1e-9 #Assume data bit period is 1ns.

#Build eye & use tstart to center data.
eye = buildeye(x, y, tbit, 2.0*tbit, tstart=0.2*tbit)

plot(eye.vx, eye.vy)
```
