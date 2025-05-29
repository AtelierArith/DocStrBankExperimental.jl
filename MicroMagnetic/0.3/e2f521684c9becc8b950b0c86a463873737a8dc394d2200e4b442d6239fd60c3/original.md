```
save_ovf(sim::AbstractSim, fname::String; type::DataType = Float64)
```

Save spins by ovf, which can be viewed by Muview. 

Parameters:

```
Sim : Sim struct whose spin to be saved.

fname : Save file name.
```

Optional:

```
type : Data type of ovf2 file. Can be chosen from Float32, Float64 or String.
```

For example:

````
```julia
    save_ovf(sim, "ovf_example")
```
````

Or to specify a certain data type:

````
```julia
    save_ovf(sim, "ovf_example", type = String)
```
````
