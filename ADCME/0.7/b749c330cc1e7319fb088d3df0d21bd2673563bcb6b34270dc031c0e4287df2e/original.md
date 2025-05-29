```
set_shape(o::PyObject, s::Union{Array{<:Integer}, Tuple{Vararg{<:Integer, N}}}) where N
set_shape(o::PyObject, s::Integer...)
```

Sets the shape of `o` to `s`. `s` must be the actual shape of `o`. This function is used to convert a  tensor with unknown dimensions to a tensor with concrete dimensions. 

# Example

```julia
a = placeholder(Float64, shape=[nothing, 10])
b = set_shape(a, 3, 10)
run(sess, b, a=>rand(3,10)) # OK 
run(sess, b, a=>rand(5,10)) # Error
run(sess, b, a=>rand(10,3)) # Error
```
