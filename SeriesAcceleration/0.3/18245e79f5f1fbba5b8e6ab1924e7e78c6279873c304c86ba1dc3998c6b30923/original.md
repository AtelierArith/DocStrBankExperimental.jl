```
esum_c(carr::AbstractArray{T1,1}, type::T2) where {T1 <: Number, T2 <: SumHelper}
```

## Desciption

Computes improved estimated for infinite series using the cumulative sum `carr` as input. The method can be chosen by setting `type`.  See also [`Richardson`](@ref), [`Shanks`](@ref). For technical reasons. the algorithm uses partial sums internally. This method therefore  provides a faster and more flexible interface, than the [`esum`](@ref) method, which will  construct the partial sums itself.

## Usage

```
esum_c(arr, r)
```

## Arguments

  * **`carr`** : `AbstractVector` of partial sum's up to each index.
  * **`type`** : Instance `SumHelper` for construction of improved estimation of the limit.

## See also

[`esum`](@ref), [`Richardson`](@ref), [`Shanks`](@ref).

## Examples

```julia
using SeriesAcceleration

r = Richardson(1:5,0:3)
arr = cumsum(S1_100 = 1 ./ (1:100) .^ 2)
limit = esum_c(arr, r)
```
