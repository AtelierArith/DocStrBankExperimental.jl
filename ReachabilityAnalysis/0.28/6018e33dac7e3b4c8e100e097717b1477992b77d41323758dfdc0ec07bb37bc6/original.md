```
BFFPSV18{N, ST, AM, IDX, BLK, RBLK, CBLK} <: AbstractContinuousPost
```

Implementation of the reachability method for linear systems using block decompositions.

## Fields

  * `δ`                – step-size of the discretization
  * `approx_model`     – (optional, default: `Forward`) approximation model;                       see `Notes` below for possible options
  * `vars`             – vector with the variables of interest
  * `block_indices`    – vector of integers to index each block that contains a variable of interest
  * `row_blocks`       – vector of integer vectors to index variables associated to blocks of interest
  * `column_blocks`    – vector of integer vectors to index variables in the partition
  * `lazy_initial_set` – (optional, default: `false`) if `true`, use a lazy decomposition of the initial states                       after discretization
  * `lazy_input`    – (optional, default: `false`) if `true`, use a lazy decomposition of the input set                     after discretization
  * `sparse`        – (optional, default: `false`) if `true`, assume that the state transition                     matrix is sparse
  * `view`          – (optional, default: `false`) if `true`, use implementation that                    uses arrays views

matrix is sparse

See the `Examples` section below for some concrete examples of these options.

## Notes

This algorithm solves the set-based recurrence equation $X_{k+1} = ΦX_k ⊕ V_k$ by using block decompositions. The algorithm was introduced in [BogomolovFFVPS18](@citet).

Comments about some fields:

  * `N`    – number type of the step-size, e.g. `Float64`
  * `ST`   – set representation used; this is either a concrete LazySet subtype,           eg. `Interval{Float64}`, or a tuple of concrete LazySet subtypes           that is commensurate with the partition

The default approximation model is:

```julia
Forward(sih=:concrete, exp=:base, setops=:lazy)
```

TODO:

  * clarify assumption about contiguous blocks

### Examples

### References

This algorithm is essentially an extension of the method in [BogomolovFFVPS18](@citet). Blocks can have different dimensions and the set representation can be different for each block.

For a general introduction we refer to the dissertation [Schilling18](@cite).

Regarding the approximation model, by default we use an adaptation of the method presented in [FrehseGDCRLRGDM11](@citet).
