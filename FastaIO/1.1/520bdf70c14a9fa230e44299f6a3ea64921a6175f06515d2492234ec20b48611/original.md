```
FastaWriter(filename::AbstractString, [mode::String = "w"])
FastaWriter([io::IO = stdout])
FastaWriter(f::Function, args...)
```

This creates an object which is able to write formatted FASTA files which conform to the specifications detailed in the section titled [The FASTA format](@ref), via the [`write`](@ref) and [`writeentry`](@ref) functions.

The third form allows to use do-notation:

```julia
FastaWriter("somefile.fasta") do fw
    # write the file
end
```

which is strongly recommended since it ensures that the [`close`](@ref) function is called at the end of writing: this is crucial, as failing to do so may result in incomplete files (this is done by the finalizer, so it will still happen automatically if the `FastaWriter` object goes out of scope and is garbage-collected, but there is no guarantee that this will happen if Julia exits).

If the `filename` ends with `.gz`, the result will be gzip-compressed.

The `mode` flag can be used to set the opening mode of the file; use `"a"` to append to an existing file.

The `FastaWriter` object has an `entry::Int` field which stores the number of the entry which is currently being written.

After creating the object, you can set the `check_description` field to `false` to disable the warning given when description lines are too long.
