```
compute!(d)
```

Computes `d.block_size` samples of signal and returns `d.outputs` (d.block*size, n*outputs).

`d.inputs` should be assigned an incoming signals matrix of dims (d.block*size, n*inputs) before calling this function.

# Examples

```julia-repl
julia> d = init!(compile("import("stdfaust.lib"); process = os.oscs(440);"));
julia> compute!(d)
256×1 Matrix{Float32}:
1.0
0.99607
0.9882256
0.9764974
0.96093166
0.9415895
0.9185469
⋮
-0.99841714
-1.0004897
-0.9986304
-0.99284655
-0.98316085
-0.96961135
-0.9522513
```
