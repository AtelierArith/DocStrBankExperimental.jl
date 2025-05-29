```
BatchView(data, batchsize; partial=true, collate=nothing)
BatchView(data; batchsize=1, partial=true, collate=nothing)
```

Create a view of the given `data` that represents it as a vector of batches. Each batch will contain an equal amount of observations in them. The batch-size can be specified using the  parameter `batchsize`. In the case that the size of the dataset is not dividable by the specified `batchsize`, the remaining observations will be ignored if `partial=false`. If  `partial=true` instead the last batch-size can be slightly smaller.

If used as an iterator, the object will iterate over the dataset once, effectively denoting an epoch. 

Any data access is delayed until iteration or indexing is perfomed.  The [`getobs`](@ref MLUtils.getobs) function is called on the data object to retrieve the observations.

For `BatchView` to work on some data structure, the type of the given variable `data` must implement the data container interface. See [`ObsView`](@ref) for more info.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`numobs`](@ref) (see Details for more information).
  * **`batchsize`** : The batch-size of each batch.   It is the number of observations that each batch must contain   (except possibly for the last one).
  * **`partial`** : If `partial=false` and the number of observations is   not divisible by the batch-size, then the last mini-batch is dropped.
  * **`collate`**: Defines the batching behavior. 

      * If `nothing` (default), a batch is `getobs(data, indices)`.
      * If `false`, each batch is `[getobs(data, i) for i in indices]`.
      * If `true`, applies MLUtils to the vector of observations in a batch,  recursively collating arrays in the last dimensions. See [`MLUtils.batch`](@ref) for more information and examples.
      * If a custom function, it will be used in place of `MLUtils.batch`. It should take a vector of observations as input.

Se also [`DataLoader`](@ref).

# Examples

```jldoctest
julia> using MLUtils

julia> X, Y = MLUtils.load_iris();

julia> A = BatchView(X, batchsize=30);

julia> @assert eltype(A) <: Matrix{Float64}

julia> @assert length(A) == 5 # Iris has 150 observations

julia> @assert size(A[1]) == (4,30) # Iris has 4 features

julia> for x in BatchView(X, batchsize=30)
           # 5 batches of size 30 observations
           @assert size(x) == (4, 30)
           @assert numobs(x) === 30
       end

julia> for (x, y) in BatchView((X, Y), batchsize=20, partial=true)
           # 7 batches of size 20 observations + 1 batch of 10 observations
           @assert typeof(x) <: Matrix{Float64}
           @assert typeof(y) <: Vector{String}
       end

julia> for batch in BatchView((X, Y), batchsize=20, partial=false, collate=false)
           # 7 batches of size 20 observations
           @assert length(batch) == 20
           x1, y1 = batch[1]
       end

julia> function collate_fn(batch)
           # collate observations into a custom batch
           return hcat([x[1] for x in batch]...), join([x[2] for x in batch])
        end;

julia> for (x, y) in BatchView((rand(10, 4), ["a", "b", "c", "d"]), batchsize=2, collate=collate_fn)
           @assert size(x) == (10, 2)
           @assert y isa String
       end
```
