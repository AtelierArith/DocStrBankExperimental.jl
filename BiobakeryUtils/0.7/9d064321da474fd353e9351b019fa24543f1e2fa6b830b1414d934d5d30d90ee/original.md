```
humann(inputfile, output[, flags]; kwargs...)
```

Run `humann` command line tool on `inputfile`, putting outputs in `output`. Requires `humann` to be installed and accessible in the `PATH` (see [Getting Started](@ref)).

`humann` flag options (those that don't have a parameter) can be passed in an array, and other options can be passed with keyword arguments. For example, if on the command line you would run:

```sh
$ humann -i $INPUTFILE -o $OUTPUT --bypass-tranlated-search --input-format fastq.gz --output-format biom
```

using this function, you would write:

```julia
humann(INTPUTFILE, OUTPUT, ["bypass_translated_search"]; input_formal="fastq.gz", output_format="biom")
```
