```
BOX{N, AM, S, D, R} <: AbstractContinuousPost
```

Implementation of a reachability method for linear systems using box approximations.

## Fields

  * `δ`            – step-size of the discretization
  * `approx_model` – (optional, default: `Forward`) approximation model;                   see `Notes` below for possible options
  * `static`
  * `dim`          – (optional default: `missing`) ambient dimension
  * `recursive`    – (optional default: `false`) if `true`, use the implementation that                   recursively computes each reach-set; otherwise, use the implementation                   that unwraps the sequence until the initial set

## Notes

The type fields are:

  * `N`  – number type of the step-size
  * `AM` – approximation model
  * `S`  – value type for the static option
  * `D`  – value type for the dimension
  * `R`  – value type for the recursive option

The default approximation model is:

```julia
Forward(sih=:concrete, exp=:base, setops=:lazy)
```

This algorithm solves the set-based recurrence equation $X_{k+1} = ΦX_k ⊕ V_k$ by computing a tight hyperrectangular over-approximation of $X_{k+1}$ at each step $k ∈ \mathbb{N}$. The recursive implementation uses the previously computed set $X_k$ to compute $X_{k+1}$. However, it is known that this method incurs wrapping effects. The non-recursive implementation instead computes $X_{k+1}$ by unwrapping the discrete recurrence until $X_0 = Ω₀$, at the expense of computing powers of the matrix $Φ$. These ideas are discussed in [BogomolovFFVPS18](@citet).

### References

This algorithm is essentially a non-decomposed version of the method in [BogomolovFFVPS18](@citet), using hyperrectangles as set representation. For a general introduction we refer to the dissertation [LeGuernicG09](@cite).

Regarding the approximation model, by default we use an adaptation of the method presented in [FrehseGDCRLRGDM11](@citet).
