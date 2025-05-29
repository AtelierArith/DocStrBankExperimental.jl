```
@tracepoint "name" color=<color> enabled=<expr> <expression>
```

Code you'd like to trace should be wrapped with `@tracepoint`

```julia
@tracepoint "name" <expression>
```

Typically the expression will be a `begin-end` block:

```julia
@tracepoint "data aggregation" begin
    # lots of compute here...
end
```

The name of the tracepoint must be a literal string, and it cannot be changed at runtime. The tracepoint can be dynamically disabled or enabled by using the `enabled` keyword argument which should be a boolean expression.

The (default) color of the zone can be configured with the `color` keyword argument to the macro which should be a literal that can either be:

  * An integer: The hex code of the color as `0xRRGGBB`.
  * A symbol: Can take the value `:black`, `:blue`, `:green`, `:cyan`, `:red`, `:magenta`, `:yellow`, `:white`, `:light_black`, `:light_blue`, `:light_green`, `:light_cyan`, `:light_red`, `:light_magenta`, `:light_yellow`, `:light_white`.
  * A tuple of three integers: The RGB value `(R, G, B)` where each value is in the range 0..255.

You can also trace function definitions where name of the tracepoint will be the name of the function unless it is explicitly provided:

```julia
@tracepoint function f(x)
    x^2
end

@tracepoint "calling g" g(x) = x^2

h = @tracepoint x -> x^2
```

If you don't have Tracy installed, you can install `TracyProfiler_jll` and start it with `run(TracyProfiler_jll.tracy(); wait=false)`.

```jldoctest
julia> x = rand(10,10);

julia> @tracepoint "multiply" x * x;

julia> @tracepoint "pow2" color=:green x^2; # green

julia> @tracepoint "pow3" color=:0xFF0000 x^3; # red

julia> @tracepoint "pow4" color=(255, 165, 0) x^4; # orange

julia> timings_enabled() = rand() < 0.5;

julia> @tracepoint "pow5" enabled=timings_enabled() x^5; # enabled only if timings_enabled() is true
```

If you don't have Tracy installed, you can install `TracyProfiler_jll` and start it with `run(TracyProfiler_jll.tracy(); wait=false)`.
