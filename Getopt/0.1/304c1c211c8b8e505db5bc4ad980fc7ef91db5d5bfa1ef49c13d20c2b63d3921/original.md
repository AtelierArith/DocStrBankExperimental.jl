```
getopt(args::Array{String}, ostr::String, longopts::Array{String}=String[])
```

Iterate through command line options with a getopt-like interface and remove options from `args`.

`args` is typically `ARGS`. By default, options are allowed to occur after non-option arguments. If `ostr[1]=='+'`, the default behavior is disabled.

# Examples

```julia
for (opt, arg) in Getopt.getopt(ARGS, "xy:", ["foo", "bar="])
	@show (opt, arg)
end
@show ARGS # only non-option arguments remain
```
