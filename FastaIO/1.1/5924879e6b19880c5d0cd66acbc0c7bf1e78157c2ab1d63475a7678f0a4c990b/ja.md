```
readentry(fr::FastaReader)
```

この関数は、エントリを1つずつ読み取るために使用できます：

```julia
fr = FastaReader("somefile.fasta")
name, seq = readentry(fr)
```

[`eof`](@ref) 関数も参照してください。
