```
vesselPhantom(N::NTuple{D,Int}; oversampling=2, kargs...)
```

Generate a random vessel phantom.

# Arguments

  * N: Image size, given as a D tuple
  * oversampling: Oversampling factor for the phantom. Default is 2.
  * rng: Random number generator
  * kernelWidth: Width (standard deviation) of the Gaussian kernel (in pixel) used for smoothing the phantom. If nothing is given, a random value is chosen.
  * kargs...: remaining keyword arguments for `vesselPath`

# Examples

using GLMakie, TrainingPhantoms, StableRNGs

im = vesselPhantom((51,51,51);            start=(1, 25, 25), angles=(0.0, 0.0),            diameter=2.5, splitProb=0.4, changeProb=0.3,            maxChange=0.3, splitnr=1, maxNumSplits=1, rng StableRNG(123));

f = Figure(size=(300,300))   ax = Axis3(f[1,1], aspect=:data)   volume!(ax, im, algorithm=:iso, isorange=0.13, isovalue=0.3, colormap=:viridis, colorrange=[0.0,0.2])
