```
BFGS!(sess::PyObject, loss::PyObject, max_iter::Int64=15000; 
vars::Array{PyObject}=PyObject[], callback::Union{Function, Nothing}=nothing, method::String = "L-BFGS-B", kwargs...)
```

`BFGS!` is a simplified interface for **L-BFGS-B** optimizer. See also [`ScipyOptimizerInterface`](@ref). `callback` is a callback function with signature 

```julia
callback(vs::Array, iter::Int64, loss::Float64)
```

`vars` is an array consisting of tensors and its values will be the input to `vs`.

# Example 1

```julia
a = Variable(1.0)
loss = (a - 10.0)^2
sess = Session(); init(sess)
BFGS!(sess, loss)
```

# Example 2

```julia
θ1 = Variable(1.0)
θ2 = Variable(1.0)
loss = (θ1-1)^2 + (θ2-2)^2
cb = (vs, iter, loss)->begin 
    printstyled("[#iter $iter] θ1=$(vs[1]), θ2=$(vs[2]), loss=$loss\n", color=:green)
end
sess = Session(); init(sess)
cb(run(sess, [θ1, θ2]), 0, run(sess, loss))
BFGS!(sess, loss, 100; vars=[θ1, θ2], callback=cb)
```

# Example 3

Use `bounds` to specify upper and lower bound of a variable. 

```julia
x = Variable(2.0)    
loss = x^2
sess = Session(); init(sess)
BFGS!(sess, loss, bounds=Dict(x=>[1.0,3.0]))
```

!!! note
    Users can also use other scipy optimization algorithm by providing `method` keyword arguments. For example, you can use the BFGS optimizer 

    ```julia
    BFGS!(sess, loss, method = "BFGS")
    ```

