```
tanhshrink(x) = x - tanh(x)
```

See ["Tanhshrink Activation Function"](https://www.gabormelli.com/RKB/Tanhshrink_Activation_Function).

```julia-repl
julia> lineplot(tanhshrink, -3, 3, height=7)
           ┌────────────────────────────────────────┐              
         3 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ tanhshrink(x)
           │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⡠⠤⠖⠊│              
           │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⢀⣀⡠⠤⠒⠊⠉⠁⠀⠀⠀⠀│              
   f(x)    │⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⢤⣤⡤⠤⠤⠤⠤⠤⠤⡷⠶⠶⠶⠶⠶⠮⠭⠥⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤│              
           │⠀⠀⠀⠀⠀⣀⡠⠴⠒⠊⠉⠁⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│              
           │⡠⠴⠒⠊⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│              
        -3 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│              
           └────────────────────────────────────────┘              
           ⠀-3⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀3⠀              
           ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀x⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀              

julia> tanhshrink.((-10f0, 10f0))
(-9.0f0, 9.0f0)
```
