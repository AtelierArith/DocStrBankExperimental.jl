```
getobs(data, [idx])
```

Return the observations corresponding to the observation index `idx`.

The index `idx` is an integer with values in the range `1:numobs(data)`. Types can optionally support `idx` being an array of integers.

If `data` does not have `getobs` defined, then in the case of `Tables.table(data) == true` returns the row(s) in position `idx`, otherwise returns `data[idx]`.

Authors of custom data containers should implement `Base.getindex` for their type instead of `getobs`. `getobs` should only be implemented for types where there is a difference between `getobs` and `Base.getindex` (such as multi-dimensional arrays).

The returned observation(s) should be in the form intended to be passed as-is to some learning algorithm. There is no strict interface requirement on how this "actual data" must look like. Every author behind some custom data container can make this decision themselves. The output should be consistent when `idx` is a scalar vs vector.

`getobs` supports by default nested combinations of array, tuple, named tuples, and dictionaries. 

The return from `getobs` should always be a materialized object, not a view, altough it can be a reference to the original data. 

If the argument `idx` is not provided, `getobs(data)` should return a materialized version of the data.

See also [`getobs!`](@ref) and [`numobs`](@ref).

# Examples

```jldoctest
julia> x = (a = [1, 2, 3], b = rand(6, 3));

julia> getobs(x, 2) == (a = 2, b = x.b[:, 2])
true

julia> getobs(x, [1, 3]) == (a = [1, 3], b = x.b[:, [1, 3]])
true

julia> x = Dict(:a => [1, 2, 3], :b => rand(6, 3));

julia> getobs(x, 2) == Dict(:a => 2, :b => x[:b][:, 2])
true

julia> getobs(x, [1, 3]) == Dict(:a => [1, 3], :b => x[:b][:, [1, 3]])
true

julia> struct DummyDataset end

julia> MLCore.numobs(d::DummyDataset) = 10

julia> MLCore.getobs(d::DummyDataset) = [1:10;] 

julia> MLCore.getobs(d::DummyDataset, i::Int) = 0 < i <= numobs(d) ? i : throw(ArgumentError("Index out of bounds"))
```
