Speed up iteratively executed code fragments with many matrix operations by transforming code in such a way that preserves arrays allocated for intermediate results, and re-use them for subsequent iterations.

First variant:

```julia
@recycle <code to be optimized>
```

Second variant:

```julia
@recycle(arrays = [<list of array variables>], funops = [<list of funop variables], numbers = [<list of number variables>], <code to be optimized>)
```

The **first variant** is the more convenient one that tries to guess the type of variables (the other variant requires its user to declare explicitly the list of variables which are type of Array, FunOp, and Number. As a tradeoff, this variant fails when the optimized code contains either a closure or non-const global variable.

The **second variant** is the more flexible (and also more verbose) one one that requires its user to declare explicitly the list of variables which are type of Array, FunOp, and Number. The other variant tries to guess the type of variables, thus it is more convenient, but as a tradeoff, that variant fails when the optimized code contains either a closure or non-const global variable. On the other hand, this (more verbose) variant is free from these limitations. *Note: All of the "keyword arguments" are optional, and also their order is arbitrary.*

An example to first variant: This function

```julia
function foo()
    A = rand(100,100)
    B = rand(100,100)
    @recycle for i = 1:5
        A += A / 2 + B
        C = A * B + 5
    end
end
```

is turned into the following:

```julia
function foo()
    A = rand(100,100)
    B = rand(100,100)
    (C, 🔃₂) = fill(nothing, 2)
    (is_first_run₁,) = fill(true, 1)
    for i = 1:5
        A .+= A ./ 2 .+ B
        if is_first_run₁
            is_first_run₁ = false
            🔃₂ = A * B
            C = 🔃₂ .+ 5
        else
            mul!(🔃₂, A, B)
            C .= 🔃₂ .+ 5
        end
    end
end
```

Another example showing what second variant can do (and the first can't):

```julia
bar = @recycle(arrays=[A,B], (A, B) -> begin
    A += A / 2 + B
    B = A * B .+ 5
end)
function baz()
    A = rand(100,100)
    B = rand(100,100)
    for i = 1:5
        bar(A,B)
    end
end
```

is turned into the following:

```julia
bar = begin
    (🔃₁,) = fill(nothing, 1)
    (is_first_run₁,) = fill(true, 1)
    (A, B)->begin
            A .+= A ./ 2 .+ B
            begin
                if is_first_run₁
                    is_first_run₁ = false
                    🔃₁ = A * B
                else
                    mul!(🔃₁, A, B)
                end
                B .= 🔃₁ .+ 5
            end
        end
end
function baz()
    A = rand(100,100)
    B = rand(100,100)
    for i = 1:5
        bar(A,B)
    end
end
```
