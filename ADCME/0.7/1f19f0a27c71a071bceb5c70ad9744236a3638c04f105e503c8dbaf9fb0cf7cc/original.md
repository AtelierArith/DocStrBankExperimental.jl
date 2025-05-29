```
BatchNormalization(dims::Int64=2; kwargs...)
```

Creates a batch normalization layer. 

# Example

```julia
b = BatchNormalization(2)
x = rand(10,2)
training = placeholder(true)
y = b(x, training)
run(sess, y)
```
