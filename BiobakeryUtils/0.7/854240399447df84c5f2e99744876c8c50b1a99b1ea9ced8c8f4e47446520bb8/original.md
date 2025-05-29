```
kneaddata(inputfile, outputfile; kwargs...)
```

Run `kneaddata` command line tool on `inputfile`, creating `outputfile`. Requires `kneaddata` to be installed and accessible in the `PATH` (see [Getting Started](@ref)).

`kneaddata` options can be passed via keyword arguments. For example, if on the command line you would run:

```sh
$ kneaddata -i some.fastq.gz -o test --n 8 --bypass-trim
```

using this function, you would write:

```julia
kneaddata("some.fastq.gz", "test"; n = 8, bypass_trim=true)
```

To pass multiple databases, pass an array of paths to the `reference_db` argument

Conda installations of `trimmomatic` (a dependency of `kneaddata`) don't work properly out of the box. If you have installed `kneaddata` using commandline conda (instead of `Conda.jl`), use `trimmomatic = /path/to/trimmomatic`, where `/path/to/trimmomatic` is something like `/home/username/miniconda3/envs/biobakery3/share/trimmomatic`. If you used `BiobakeryUtils.install_deps()`, you don't need to worry about this.
