```
@unitdim(U::UnitSystem,F,M,L,T,Q,Θ,N,J="lm",A="rad")
```

Specify the `print` output for each base dimension of `U::UnitSystem` with `String` input arguments `force`, `mass`, `length`, `time`, `charge`, `temperature`, `molaramount`, `luminousflux`, `angle`.

```Julia
@unitdim Gauss "gf" "g" "cm" "s" "C" "K" "mol"
@unitdim Metric "kgf" "kg" "m" "s" "C" "K" "mol"
@unitdim British "lb" "slug" "ft" "s" "C" "°R" "slug-mol"
@unitdim IPS "lb" "slinch" "in" "s" "C" "°R" "slinch-mol"
@unitdim FPS "pdl" "lb" "ft" "s" "C" "°R" "lb-mol"
@unitdim English "lbf" "lbm" "ft" "s" "C" "°R" "lb-mol"
@unitdim IAU☉ "M☉f" "M☉" "au" "D" "C" "K" "mol"
```

These standard examples are some of the built-in defaults.
