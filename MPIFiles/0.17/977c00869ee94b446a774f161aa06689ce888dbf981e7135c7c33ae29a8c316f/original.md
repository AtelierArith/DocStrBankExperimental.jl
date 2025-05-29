```julia
TransferFunction(filename::String; kargs...) -> Any

```

Create a `TransferFunction` from a data file at `filename`.

The file can be either a h5-File created with this package or a file that is written by a VNA. Keyword arguments will be passed to `load_tf_fromVNA` 
