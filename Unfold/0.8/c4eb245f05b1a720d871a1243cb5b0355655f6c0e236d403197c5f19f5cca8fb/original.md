```julia
hrfbasis(TR; parameters, name)

```

Generate a Hemodynamic-Response-Functio (HRF) basis with inverse-samplingrate "TR" (=1/FS)

Optional Parameters p:                                                            defaults                                                           {seconds}         p(1) - delay of response (relative to onset)          6         p(2) - delay of undershoot (relative to onset)       16         p(3) - dispersion of response                         1         p(4) - dispersion of undershoot                       1         p(5) - ratio of response to undershoot                6         p(6) - onset {seconds}                                0         p(7) - length of kernel {seconds}                    32

# Examples

Generate a HRF basis function object with Sampling rate 1/TR. And evaluate it at an event occuring at TR 103.3 with duration of 4.1 TRs

```julia-repl
julia>  f = hrfbasis(2.3)
julia>  f(103.3,4.1)

```
