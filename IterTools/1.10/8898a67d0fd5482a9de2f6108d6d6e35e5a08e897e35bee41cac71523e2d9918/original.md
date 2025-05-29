```
subsets(xs)
subsets(xs, k)
subsets(xs, Val{k}())
```

Iterate over every subset of the indexable collection `xs`. You can restrict the subsets to a specific size `k`.

Giving the subset size in the form `Val{k}()` allows the compiler to produce code optimized for the particular size requested. This leads to performance comparable to hand-written loops if `k` is small and known at compile time, but may or may not improve performance otherwise.

```jldoctest
julia> for i in subsets([1, 2, 3])
          @show i
       end
i = Int64[]
i = [1]
i = [2]
i = [1, 2]
i = [3]
i = [1, 3]
i = [2, 3]
i = [1, 2, 3]

julia> for i in subsets(1:4, 2)
          @show i
       end
i = [1, 2]
i = [1, 3]
i = [1, 4]
i = [2, 3]
i = [2, 4]
i = [3, 4]

julia> for i in subsets(1:4, Val{2}())
           @show i
       end
i = (1, 2)
i = (1, 3)
i = (1, 4)
i = (2, 3)
i = (2, 4)
i = (3, 4)
```
