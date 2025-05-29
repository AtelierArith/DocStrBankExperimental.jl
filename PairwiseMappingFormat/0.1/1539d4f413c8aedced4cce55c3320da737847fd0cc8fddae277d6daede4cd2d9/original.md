```
PAFReader(io::IO; copy::Bool=true)
```

Construct a `PAFReader`, an iterator of [`PAFRecord`](@ref) read from `io`. Iterating this object returns a `PAFRecord` for each valid line of input, and throws a [`ParserException`](@ref) when an invalid record is found. For efficiency, the auxiliary fields are not validated until they are accessed.

If `copy` is false, the *same* record will be returned on each iteration, with its content being overwritten. This removes a few allocations per iteration, but may cause problems if records of old iterations are stored.

# Examples

```jldoctest
julia> reader = PAFReader(open(path_to_paf)); typeof(reader)
PAFReader{IOStream}

julia> typeof(first(reader))
PAFRecord

julia> PAFReader(open(path_to_paf)) do reader
           for record in reader
                println(record.qlen)
           end
       end
301156
299273
288659

julia> PAFReader(open(path_to_paf); copy=false) do reader
           fst = first(reader)
           all(reader) do record
               record === fst
           end
       end
true
```

See also: [`PAFRecord`](@ref), [`try_next!`](@ref)
