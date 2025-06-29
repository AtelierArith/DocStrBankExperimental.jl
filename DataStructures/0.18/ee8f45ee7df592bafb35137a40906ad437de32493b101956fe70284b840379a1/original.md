```
OrderedRobinDict([itr])
```

`OrderedRobinDict{K,V}()` constructs a ordered dictionary with keys of type `K` and values of type `V`. It takes advantage of `RobinDict` in maintaining the order of the keys. Given a single iterable argument, constructs a [`OrderedRobinDict`](@ref) whose key-value pairs are taken from 2-tuples `(key,value)` generated by the argument.

# Examples

```jldoctest
julia> OrderedRobinDict([("A", 1), ("B", 2)])
OrderedRobinDict{String, Int64} with 2 entries:
  "A" => 1
  "B" => 2
```

Alternatively, a sequence of pair arguments may be passed.

```jldoctest
julia> OrderedRobinDict("A"=>1, "B"=>2)
OrderedRobinDict{String, Int64} with 2 entries:
  "A" => 1
  "B" => 2
```
