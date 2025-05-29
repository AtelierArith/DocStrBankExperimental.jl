```
construct_reader_shallow(S,array_specs)
```

Generates a `Base.read(io::IOStream, ::Type{S})` method that can used read type `S`, which is not an `isbitstype`.  The named tuble, `array_spec`, is used to define the dimensionality of the field in question. 

# Example

```julia-repl
julia> struct CompoundStruct
           long::Float32
           COG::UInt16
           data::Matrix{Float64}
       end
julia> construct_reader_shallow(CompoundStruct, (data=(10,10),))
```

The above will generate a suitable `read` method assuming that the `data` field is a 10x10 matrix. 

See also: `construct_reader_deep`, `@construct_reader`
