```
SSHT(s, ℓₘₐₓ; [method="Direct"], [T=Float64], [kwargs...])
```

Construct an `SSHT` object to transform between spin-weighted spherical-harmonic mode weights and function values — performing an $s$-SHT.

This object behaves similarly to an `AbstractFFTs.Plan` object — specifically in the ability to use the semantics of algebra to perform transforms.  For example, if the function values are stored as a vector `f`, the mode weights as `f̃`, and the `SSHT` as `𝒯`, then we can compute the function values from the mode weights as

```
f = 𝒯 * f̃
```

or solve for the mode weights from the function values as

```
f̃ = 𝒯 \ f
```

The first dimensions of `f̃` must index the mode weights (as usual, for `ℓ∈abs(s):ℓₘₐₓ` and `m∈-ℓ:ℓ`) and the first index of `f` must index the locations at which the function is evaluated.  Any following dimensions will be broadcast over.  Note that certain types will broadcast using Julia threads, while others will broadcast using BLAS threads.  The relevant number of threads must be set appropriately.

Certain `SSHT` types (currently, only `Minimal` and `Direct`) also have an option to *always* act in place — meaning that they simply re-use the input storage, even when used in an expression like `𝒯 \ f`.  The option must be passed as the `inplace` argument to the constructors, and is part of the type of the resulting object.  Regardless of the value of that option, for those types where the option exists, it is also possible to use `mul!` and `ldiv!` from the `LinearAlgebra` package to force operation in place.

Note that different algorithms require different "pixelizations", or sets of `Rotor`s on which to evaluate the function.  These can be obtained from the `SSHT` object using the [`pixels`](@ref) and [`rotors`](@ref) functions.
