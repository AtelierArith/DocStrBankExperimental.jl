```
readentry(fr::FastaReader)
```

This function can be used to read entries one at a time:

```julia
fr = FastaReader("somefile.fasta")
name, seq = readentry(fr)
```

See also the [`eof`](@ref) function.
