```
@>>(code)
```

Rewrites code using the same rewriting rules as @> only the first element of the pipe is not  rewritten and is instead passed through the pipe. 

The functions are created using the following rules:

1. Underscores are treated as the function argument. `@>> [1,2,3] |> sum(_)` is equivalent to

`[1,2,3] |> x -> sum(x)`

2. If the is no underscore in the expression then then the the first argument is imputed,

`@>> [1,2,3] |> .+(3)` is equivalent to `[1,2,3] |> x -> .+(x, 3)`

3. If expression is symbol then it is treated as function so `@> "hello world" |> print` is interpreted as

`"hello world" |> x -> print(x)`

4. The above 2 rules are applied to expressions separated by the pipe operator, `|>`. Hence

`@>> 1 |> [_, 1, 2] |> sum()` is equivalent to `1 |> x -> [x, 1, 2] |> x -> sum(x)`

5. These rules also applied to macros, with the exception of @> and @>>. Hence `@>> "hello world" |> @show`

is equivalent to `@>> "hello world" |> @show(_)` 

6. The macro can also be used in itself. If the @>> appears within itself or @> and _ is in the first

section of the pipe then it comes from the surrounding context. See the example below.  

7. Instead of pipe characters, |>, separating the different functions that to be created a `begin ... end`

block can be used with and separate function is created for each line in the block. See the example below. 

7. If there is a sequence of pipe characters within a sequence of pipe characters then a new pipe is

is created if the first part of the pipe does not contain an underscore so @>> 1 |> [_, 2, sqrt(36) |> _/2] is equivalent to 1 |> x -> [x, 3, sqrt(36) |> y -> y/2]. 

Examples: 

```julia-repl
julia> @>> 1 |>
            [(@>> _ |> +(1, 2)), 1, 1] |>
            sum
6
```

```julia-repl
julia> @>> begin 
            1 
            [(@>> _ |> _ + 2), 1, 1] 
            sum
        end
5
```
