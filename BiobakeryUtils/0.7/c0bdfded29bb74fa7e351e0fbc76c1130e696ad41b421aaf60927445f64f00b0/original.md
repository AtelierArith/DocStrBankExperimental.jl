```
metaphlan(inputfile, outputfile; kwargs...)
```

Run `metaphlan` command line tool on `inputfile`, creating `outputfile`. Requires `metaphlan` to be installed and accessible in the `PATH` (see [Getting Started](@ref)).

`metaphlan` options can be passed via keyword arguments. For example, if on the command line you would run:

```sh
$ metaphlan some.fastq.gz output/some_profile.tsv --input_type fastq --nproc 8
```

using this function, you would write:

```julia
metaphlan("some.fastq.gz", "output/some_profile.tsv"; input_type="fastq", nproc=8)
```

Note: the `input_type` keyword is required.

Set the environmental variable `"METAPHLAN_BOWTIE2_DB"``to specify the location where the markergene database is/will be installed, or pass`bowtie2db = "some/path"` as a keyword argument.
