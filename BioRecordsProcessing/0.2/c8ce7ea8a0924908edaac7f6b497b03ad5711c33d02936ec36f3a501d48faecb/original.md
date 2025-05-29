```julia
Writer(record_module::Module, output_directory::String; 
    suffix = "", 
    paired = false, 
    second_in_pair = nothing, 
    extension = nothing, 
    header = nothing
)
```

Write the output of the processing function into a file, the first argument is the module that owns the `Record` type (e.g `FASTX.FASTA`, `VCF`, ...), and the second the ouput directory. The filename is determined by the source, to which an optional suffix can be added.  If the type ouput is different from the type of the output (e.g. SAM to BAM), the extension (".bam") should be specified. For SAM & BAM a SAM.Header should be provided.

To avoid overwriting existing files, the pipeline will check that the output file is different from the input file.
