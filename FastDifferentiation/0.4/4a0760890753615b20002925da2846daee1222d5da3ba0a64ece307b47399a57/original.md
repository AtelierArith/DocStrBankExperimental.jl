```
make_function(
    func_array::AbstractArray{<:Node},
    input_variables::AbstractVector{<:Node}...;
    in_place::Bool=false, init_with_zeros::Bool=true
)
```

Makes a function to evaluate the symbolic expressions in `func_array`. Every variable that is used in `func_array` must also be in `input_variables`. However, it will not cause an error if variables in `input_variables` are not variables used by `func_array`.

```julia
julia> @variables x
x

julia> f = x+1
(x + 1)


julia> jac = jacobian([f],[x]) #the Jacobian has a single constant element, 1, and is no longer a function of x
1×1 Matrix{FastDifferentiation.Node}:
 1

 julia> fjac = make_function(jac,[x])
 ...
 
 julia> fjac(2.0) #the value 2.0 is passed in for the variable x but has no effect on the output. Does not cause a runtime exception.
 1×1 Matrix{Float64}:
  1.0
```

If `in_place=false` then a new array will be created to hold the result each time the function is called. If `in_place=true` the function expects a user supplied array to hold the result. The user supplied array must be the first argument to the function.

```julia
julia> @variables x
x

julia> f! = make_function([x,x^2],[x],in_place=true)
...

julia> result = zeros(2)
2-element Vector{Float64}:
 0.0
 0.0

julia> f!(result,[2.0])
4.0

julia> result
2-element Vector{Float64}:
 2.0
 4.0
```

If the array is sparse then the keyword argument `init_with_zeros` has no effect. If the array is dense and `in_place=true` then the keyword argument `init_with_zeros` affects how the in place array is initialized. If `init_with_zeros = true` then the in place array is initialized with zeros. If `init_with_zeros=false` it is the user's responsibility to initialize the array with zeros before passing it to the runtime generated function.

This can be useful for modestly sparse dense matrices with say at least 1/4 of the array entries non-zero. In this case a sparse matrix may not be as efficient as a dense matrix. But a large fraction of time could be spent unnecessarily setting elements to zero. In this case you can initialize the in place Jacobian array once with zeros before calling the run time generated function.
