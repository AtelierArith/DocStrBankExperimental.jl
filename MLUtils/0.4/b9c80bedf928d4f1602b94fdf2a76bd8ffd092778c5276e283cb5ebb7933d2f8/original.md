```
mapobs(f, d::DataLoader)
```

Return a new dataloader based on `d`  that applies `f` at each iteration. 

# Examples

```jldoctest
julia> X = ones(3, 6);

julia> function f(x)
           @show x
           return x
       end
f (generic function with 1 method)

julia> d = DataLoader(X, batchsize=2, collate=false);

julia> d = mapobs(f, d);

julia> for x in d
           @assert size(x) == (2,)
           @assert size(x[1]) == (3,)
       end
x = [[1.0, 1.0, 1.0], [1.0, 1.0, 1.0]]
x = [[1.0, 1.0, 1.0], [1.0, 1.0, 1.0]]
x = [[1.0, 1.0, 1.0], [1.0, 1.0, 1.0]]

julia> d2 = DataLoader(X, batchsize=2, collate=true);

julia> d2 = mapobs(f, d2);

julia> for x in d2
           @assert size(x) == (3, 2)
       end
x = [1.0 1.0; 1.0 1.0; 1.0 1.0]
x = [1.0 1.0; 1.0 1.0; 1.0 1.0]
x = [1.0 1.0; 1.0 1.0; 1.0 1.0]
```
