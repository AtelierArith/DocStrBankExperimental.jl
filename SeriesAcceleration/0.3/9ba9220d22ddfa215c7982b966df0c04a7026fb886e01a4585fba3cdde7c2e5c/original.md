```
esum(arr::AbstractArray{T1,1}, type::T2) where {T1 <: Number, T2 <: SumHelper}
```

## Desciption

Computes improved estimated for infinite series using the summands of the series `arr`, as input. The method can be chosen by setting `type`.  In cases where the cumulative sum can not be naively computed, one can also specify a function `csum_f` to obtain the 1 dimensional array of partial sums.

## Usage

```
esum(arr, r)
```

## Arguments

  * **`arr`**    : `AbstractVector` of summands.
  * **`type`**   : Instance `SumHelper` for construction of improved estimation of the limit.
  * **`csum_f`** : Optional. Function which constructs partial sum array from `arr`.

## See also

[`esum_c`](@ref), [`Richardson`](@ref), [`Shanks`](@ref).

## Examples

```julia
using SeriesAcceleration

r = Richardson(1:5,0:3)
arr = S1_100 = 1 ./ (1:100) .^ 2
limit = esum(arr, r)
```
