```
DataLoader(data; [batchsize, buffer, collate, parallel, partial, rng, shuffle])
```

An object that iterates over mini-batches of `data`, each mini-batch containing `batchsize` observations (except possibly the last one).

Takes as input a single data array, a tuple (or a named tuple) of arrays, or in general any `data` object that implements the [`numobs`](@ref) and [`getobs`](@ref) methods.

The last dimension in each array is the observation dimension, i.e. the one divided into mini-batches.

The original data is preserved in the `data` field of the DataLoader.

# Arguments

  * **`data`**: The data to be iterated over. The data type has to be supported by [`numobs`](@ref) and [`getobs`](@ref).
  * **`batchsize`**: If less than 0, iterates over individual observations. Otherwise, each iteration (except possibly the last) yields a mini-batch containing `batchsize` observations. Default `1`.
  * **`buffer`**: If `buffer=true` and supported by the type of `data`, a buffer will be allocated and reused for memory efficiency. May want to set `partial=false` to avoid size mismatch.  Finally, can pass an external buffer to be used in `getobs!` (depending on the `collate` and `batchsize` options, could be `getobs!(buffer, data, idxs)` or `getobs!(buffer[i], data, idx)`). Default `false`.
  * **`collate`**: Defines the batching behavior. Default `nothing`. 

      * If `nothing` , a batch is `getobs(data, indices)`.
      * If `false`, each batch is `[getobs(data, i) for i in indices]`.
      * If `true`, applies `MLUtils.batch` to the vector of observations in a batch,  recursively collating arrays in the last dimensions. See [`MLUtils.batch`](@ref) for more information and examples.
      * If a custom function, it will be used in place of `MLUtils.batch`. It should take a vector of observations as input.
  * **`parallel`**: Whether to use load data in parallel using worker threads. Greatly   speeds up data loading by factor of available threads. Requires starting   Julia with multiple threads. Check `Threads.nthreads()` to see the number of   available threads. **Passing `parallel = true` breaks ordering guarantees**.   Default `false`.
  * **`partial`**: This argument is used only when `batchsize > 0`. If `partial=false` and the number of observations is not divisible by the batchsize, then the last mini-batch is dropped. Default `true`.
  * **`rng`**: A random number generator. Default `Random.default_rng()`.
  * **`shuffle`**: Whether to shuffle the observations before iterating. Unlike   wrapping the data container with `shuffleobs(data)`, `shuffle=true` ensures   that the observations are shuffled anew every time you start iterating over   `eachobs`. Default `false`.

# Examples

```jldoctest
julia> Xtrain = rand(10, 100);

julia> array_loader = DataLoader(Xtrain, batchsize=2);

julia> for x in array_loader
         @assert size(x) == (10, 2)
         # do something with x, 50 times
       end

julia> array_loader.data === Xtrain
true

julia> tuple_loader = DataLoader((Xtrain,), batchsize=2);  # similar, but yielding 1-element tuples

julia> for x in tuple_loader
         @assert x isa Tuple{Matrix}
         @assert size(x[1]) == (10, 2)
       end

julia> Ytrain = rand('a':'z', 100);  # now make a DataLoader yielding 2-element named tuples

julia> train_loader = DataLoader((data=Xtrain, label=Ytrain), batchsize=5, shuffle=true);

julia> for epoch in 1:100
         for (x, y) in train_loader  # access via tuple destructuring
           @assert size(x) == (10, 5)
           @assert size(y) == (5,)
           # loss += f(x, y) # etc, runs 100 * 20 times
         end
       end

julia> first(train_loader).label isa Vector{Char}  # access via property name
true

julia> first(train_loader).label == Ytrain[1:5]  # because of shuffle=true
false

julia> foreach(println∘summary, DataLoader(rand(Int8, 10, 64), batchsize=30))  # partial=false would omit last
10×30 Matrix{Int8}
10×30 Matrix{Int8}
10×4 Matrix{Int8}

julia> collate_fn(batch) = join(batch);

julia> first(DataLoader(["a", "b", "c", "d"], batchsize=2, collate=collate_fn))
"ab"
```
