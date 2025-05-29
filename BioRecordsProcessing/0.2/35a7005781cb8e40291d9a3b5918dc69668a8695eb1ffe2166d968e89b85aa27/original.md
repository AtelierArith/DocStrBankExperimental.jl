```julia
Reader(record_module::Module, file_provider::F) where {F <: AbstractFileProvider}
```

Read a file or a directory on the disk and produce records of type `record_module.Record`.  The second argument can be a `File` or a `Directory`.

If a string is passed the second argment will default to `File`.

```@example
Reader(FASTX.FASTA, "test.fa")
Reader(FASTX.FASTA, File("test.fa"))
Reader(FASTX.FASTQ, Directory("data/", "*.fastq"))
```
