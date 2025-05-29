```
sco(
    expr::AbstractString;
    pre::Function=identity,
    process::Union{Nothing,Function}=nothing,
    post::Function=identity
)
```

Show code and output for `expr`. Process the output by applying `pre`, `process` or `post` to it. Specifically,

  * `pre` is applied before `convert_output`
  * `process` is applied instead of `convert_output`
  * `post` is applied after convert output

For example, for

```julia
let
    pre(out) = Options(out; label="l")
    post = string
    sco("DataFrame(x = [1])"; pre, post)
end
```

the DataFrame will go through three stages:

1. `pre` adds the label "l" to the object
2. `process` is nothing, so `convert_output` will do its usual stuff, namely converting  the DataFrame object to Markdown.
3. `post` converts the output to a string (even though this is already done by `convert_output` in this case).

So, to disable `convert_output`, pass `process=nothing` or `process=identity`.
