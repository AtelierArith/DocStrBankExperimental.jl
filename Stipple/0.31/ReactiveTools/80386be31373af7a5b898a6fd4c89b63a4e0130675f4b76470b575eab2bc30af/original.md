```julia
@app(expr)
```

Sets up and enables the reactive variables and code provided in the expression `expr`.

**Usage**

The code block passed to @app implements the app's logic, handling the states of the UI components and the code that is executed when these states are altered.

```julia
@app begin
   # reactive variables
   @in N = 0
   @out result = 0

   # reactive code to be executed when N changes
   @onchange N begin
     result = 10 * N
   end
   
   # reactive code with explicit priority (default: 0)
   @onchange N begin
     # the exclamation mark is used to indicate that the variable is silently updated,
     # i.e. without triggering a new change event in order to avoid infinite loops
     N[!] = clamp(N, 0, 10)
   end priority = 1

   # reactive code calling a function defined outside of the `@app` block
   @onchange N on_N()
end

# Callback function defined outside of the `@app` block:
# This definition has to be placed after the `@app` block.
# This syntax is useful for including long code, which also can be moved to a separate file.
# It is also very handy for debugging and testing, as this function can be updated without
# reloading the app - in contrast to the code that is defined within the `@app` block.
@handler function on_N()
  @info "on_N() called"
end
```

Setting priority can be useful executing code before a value is being sent to the client, e.g. for range checking before triggering expensive calculations. In the example above, the value of `N` is clamped to the range [0, 10] before the result is calculated.

In any handler you can abort the handler queue by returning `Consume(true)`. In that case all pending handlers will be skipped. If a priority > 0 is set, the client will not be updated.
