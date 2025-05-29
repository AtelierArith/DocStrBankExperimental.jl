```
@>(code)
```

Rewrites code to create an anonymous function that takes one argument. Designed to pipe one object  through multiple functions. 

The functions are created using the following rules:

1. Underscores are treated as the function argument. `@> sum(_)` is equivalent to `x -> sum(x)`
2. If the is no underscore in the expression then then the the first argument is imputed,

`@> +(3)` is equivalent to `x -> +(x, 3)`

3. If expression is symbol then it is treated as function so `@> print` is interpreted as

`x -> print(x)`

4. The above 2 rules are applied to expressions separate by the pipe operator, `|>`. Hence

`@> [_, 1, 2] |> sum()` is equivalent to `x -> [x, 1, 2] |> x -> sum(x)`

5. These rules also apply to macros, with the exception of @> and @>>.`
6. The input can also be a `begin end block`. A separate function is created for each line in the

block with result of previous function passed into the next using the re-writing rules. 

7. If there is a sequence of pipe characters within a sequence of pipe characters then a new pipe is

is created if the first part of the pipe does not contain an underscore so @> [_, 2, sqrt(36) |> _/2]  is equivalent to x -> [x, 3, sqrt(36) |> y -> y/2]. 

The macro can also be used in itself. Although will often require the use of brackets to get the  desired effect. 

Examples: 

```julia-repl
julia> 1 |>
           @>  [_ |> @>(_ + 2), 1, 1] |>
               sum
5
```

```julia-repl
julia> 1 |>
           @>  begin
                [1, 1, _ |> @> +(1, 2)] 
                sum
            end
6
```
