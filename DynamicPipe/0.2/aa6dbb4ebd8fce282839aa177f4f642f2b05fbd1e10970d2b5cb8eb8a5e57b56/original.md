```
@>>(first_arg, pipe::Expr)
```

Rewrites `pipe` into an anonymous function and passes `first_arg` into it. `pipe` must be a `begin ... end` block.  A function is created for each line in the `begin ... end` block. The result of the previous function is passed  into the next. 

The pipe is created using the following rules:

1. Underscores are treated as the function argument. `@>> [1,2,3] begin sum(_) end` is equivalent to

`[1,2,3] |> x -> sum(x)`

2. If the is no underscore in the expression then then the the first argument is imputed,

`@>> [1,2,3] begin .+(3) end` is equivalent to `[1,2,3] |> x -> .+(x, 3)`

3. If expression is a symbol then it is treated as function so `@>> "hello world" begin print end` is interpreted as

`"hello world" |> x -> print(x)`

4. The above 2 rules are applied to each line of a begin end block. Hence

```
    @>> 1 begin 
        [_, 1, 2] 
        sum()
    end
```

is equivalent to `1 |> x -> [x, 1, 2] |> x -> sum(x)`

5. These rules also applied to macros, with the exception of @> and @>>. Hence `@>> "hello world" begin @show end`

is equivalent to `"hello world" |> x -> @show(x )` 

6. The macro can also be used in itself. If the @>> appears within itself or @> and _ is in the first

section of the pipe then it comes from the surrounding context. See the example below.  

7. If there is a sequence of pipe characters within a sequence of pipe characters then a new pipe is

is created if the first part of the pipe does not contain an underscore so 

`````
    @>> 1 begin  
        [_, 2, sqrt(36) |> _/2]
    end 
    
````
is equivalent to 1 |> x -> [x, 3, sqrt(36) |> y -> y/2]. 

Examples: 
`````

julia-repl julia> @>> 1 begin             [(@>> _ |> +(2)), 1, 1]              sum         end 5 ```
