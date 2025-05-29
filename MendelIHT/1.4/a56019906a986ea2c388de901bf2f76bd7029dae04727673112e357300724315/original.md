```
project_group_sparse!(y::AbstractVector, group::AbstractVector, J::Integer, k<:Real)
```

When `k` is an integer, projects the vector `y` onto the set with at most `J` active groups  and at most `k` active predictors per group. To have variable group sparsity level, input `k` as a vector of integers. We will preserve `k[1]` elements for group 1, `k[2]` predictors for  group 2...etc. This function assumes there are no unknown or overlaping group membership.

Note: In the `group` vector, the first group must be 1, and the second group must be 2...etc. 

# Examples

```julia-repl
using MendelIHT
J, k, n = 2, 3, 20
y = collect(1.0:20.0)
y_copy = copy(y)
group = rand(1:5, n)
project_group_sparse!(y, group, J, k)
for i = 1:length(y)
    println(i,"  ",group[i],"  ",y[i],"  ",y_copy[i])
end

J, k, n = 2, 0.9, 20
y = collect(1.0:20.0)
y_copy = copy(y)
group = rand(1:5, n)
project_group_sparse!(y, group, J, k)
for i = 1:length(y)
    println(i,"  ",group[i],"  ",y[i],"  ",y_copy[i])
end
```

# Arguments

  * `y`: The vector to project
  * `group`: Vector encoding group membership
  * `J`: Max number of non-zero group
  * `k`: Maximum predictors per group. Can be a positive integer or a vector of integers.
