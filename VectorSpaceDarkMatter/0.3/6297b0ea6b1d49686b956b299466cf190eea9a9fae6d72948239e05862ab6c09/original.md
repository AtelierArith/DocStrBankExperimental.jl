```
rate(R, model::ModelDMSM, pfv::ProjectedF, pfq::ProjectedF; 
    ell_max=nothing, use_measurements=false)
```

Calculates the rate for a given model, projected $g_\chi$ (`pfv`), projected  $f_s^2$ (`pfq`), and rotation `R` given as a quaternion or rotor (if you want  other rotations, see `Quaternionic.jl`'s conversion methods). `R` can also be a vector of quaternions or rotors.

The maximum $\ell$ that is used is the minimum of the specified `ell_max` and the maximum $\ell$ for each of `pfv` and `pfq`.

Using measurements here is currently slow and not recommended.
