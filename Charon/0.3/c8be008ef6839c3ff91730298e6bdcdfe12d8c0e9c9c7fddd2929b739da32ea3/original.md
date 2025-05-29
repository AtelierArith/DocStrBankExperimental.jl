```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, dicefile::IO, messages::Integer=nsteps÷100, scalingmessages::Bool=true, header::Bool=true)
```

dicefile is an opened CSV-file in DICE 2-pop format: It should contain exactly 4 columns, the first one contains the number of ancestral reads, the second the number of derived reads, the third the frequency of the derived allele in the anchor population and the fourth the number of loci with exactly this combination of data.

If you have Julia 1.3 or higher, and the file is a zipped file, open it using a zip decompressor:

```julia
using CodecZlib
dicefile = GzipDecompressorStream(open("path/to/your/file.csv.gz"))
```

With the named argument "header" one should indicate whether the CSV file has a header. The default is true.
