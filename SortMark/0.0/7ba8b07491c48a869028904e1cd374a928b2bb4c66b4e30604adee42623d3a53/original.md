```
make_df(algs = [MergeSort, QuickSort]; ...)
```

Make a dataframe where each row is a sorting task specified by the cartesian product of keyword arguments.

# Arguments

  * `algs::AbstractVector{<:Base.Sort.Algorithm} = [MergeSort, QuickSort]`:   sorting algorithms to test
  * `unstable::AbstractVector{<:Base.Sort.Algorithm} = [QuickSort]`:   which of the algorithms are allowed to be unstable

Axes of the cartesian product

  * `Types::AbstractVector{<:Type} = SortMark.BitTypes`:   element type
  * `lens::AbstractVector{<:Integer} = SortMark.lengths()`:   number of elements to be sorted
  * `orders::AbstractVector{<:Ordering} = SortMark.orders`:   orders to sort by
  * `sources::AbstractDict{<:Any, <:Function} = SortMark.sources`:   generation procedures to create input data

Benchmarking time

  * `seconds::Union{Real, Nothing} = .005`:   maximum benchmarking time for each row. Compute sum(df.seconds) for an estimated   benchmarking runtime
  * `samples::Union{Nothing, Integer} = nothing`:   maximum number of samples for each row. Compute sum(df.seconds) for an estimated   benchmarking runtime

Setting `seconds` or `samples` to `nothing` removes that limit.
