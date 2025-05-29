The usage is similar to [proconio-rs](https://github.com/statiolake/proconio-rs). You need to specify the variable name and its structure.

```julia
@input a = Int
```

Multiple variables need to be nested in a block.

```julia
@input begin
    a = Char
    b = Float32
    c = (Int, Char)
    d = String
    e = Bool
end
```

Arrays need to be specified in the form of `[type; shape]`.

```julia
@input begin
    a = [Int; 3]
    b = [Float32; (2, 3)]
end
```

Complex structures can also be handled.

```julia
@input a = [(Int, [Int; (2, 2)], Char); (2, 2)]
```

In CP, the size of arrays is usually specified by the input itself. This can be handled by using variables already read in.

Note that [ProconIO.jl](https://github.com/lucifer1004/ProconIO.jl) follows Julia's column-major convention, instead of the row-major which is commonly used in CP. So you may need to swap the row and column indices when reading the array.

```julia
@input begin
    n = Int
    m = Int
    v = [Int; (m, n)]
end
```

If you prefer a row-major flavor, you can use a vector of vectors instead.

```julia
@input begin
    n = Int
    m = Int
    v = [[Int; m]; n]
end
```

Sometimes the input is a vector of variable-length vectors. This can be handled by leaving out the shape and reading it from the input instead. The following code reads in a vector of `n` variable-length vectors.

```julia
@input begin
    n = Int
    v = [[Int; ]; n]
end
```

```
