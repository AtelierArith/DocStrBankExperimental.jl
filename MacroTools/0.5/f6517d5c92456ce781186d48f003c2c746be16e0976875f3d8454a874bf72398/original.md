```
combinedef(dict::Dict)
```

`combinedef` is the inverse of [`splitdef`](@ref). It takes a `splitdef`-like Dict and returns a function definition.

This function approximately does the following (but more sophisticated to avoid emitting parts that did not actually appear in the original function definition.)

```julia
rtype = get(dict, :rtype, :Any)
all_params = [get(dict, :params, [])..., get(dict, :whereparams, [])...]
:(function $(dict[:name]){$(all_params...)}($(dict[:args]...);
                                            $(dict[:kwargs]...))::$rtype
      $(dict[:body])
  end)
```
