```
gcb(sequences::Union{String, IO, FASTAReader, Vector{<:NucSeq}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{String}, Nothing} = nothing, ref_vector = [], perc = 0.05, rm_start = false, rm_stop = false, threshold = 80)
gcb(sequences::Union{Vector{String}, Vector{<:IO}, Vector{<:FASTAReader}, Vector{<:Vector{<:NucSeq}}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{Vector{String}}, Nothing} = nothing, ref_vectors = [], perc = 0.05, rm_start = false, rm_stop = false, threshold = 80)
```

Calculate GCB from Merkl, 2003.

# Arguments

  * `sequences`: DNA or RNA sequences to be analyzed, which should be coding sequences only. This can take quite a few forms depending on your use case. It can be a path to fasta file of coding sequences (e.g. .fasta, .fna, .fa), or a IO or FASTAReader pointing to these fasta files. It can also be a vector of BioSequences, if you've already brought them into Julia's environment. There are no quality checks, so it's assumed that each entry is assumed to be an individual coding sequence, in the correct frame, without 5' or 3' untranslated regions. If you are analyzing multiple genomes (or sets of sequences), `sequences` could instead be a vector of filepaths, IOStreams, FASTAReaders, or vectors of BioSequences, with each vector corresponding to a genome. `CUBScout` is multithreaded; if there are multiple threads available, `CUBScout` will allocate a thread for each fasta file or vector of BioSequences. As such, providing a vector of filepaths (or `Vector{<:Vector{<:NucSeq}}`) as an argument will be faster than broadcasting across a vector of paths. Because a single file is only accessed by a single thread, it's never worth using more threads than the total number of files being analyzed.
  * `dict`: codon dictionary of type `CodonDict`. The standard genetic code is loaded by default, but if necessary you can create your own codon dictionary using `make_CodonDict`
  * `names`: An optional vector of names for each sequence. Only relevant if providing a vector of BioSequences, as names are automatically pulled from fasta files. If `sequences` is of type `Vector{<:Vector{<:NucSeq}}`, `names` should be of type `Vector{Vector{String}}`
  * `ref_vector`: optional reference subset; by default gcb begins calculations using all genes as a seed. If you want to provide a custom reference set, it should be a vector `Bool[]` the same length as the number of sequences in your fasta file, and contains `true` for sequences you want as your reference subset and false for those you don't. You can use `find_seqs()` to generate this vector. If providing multiple filepaths and want custom reference sets, `ref_vectors` should be a vector of vectors corresponding to the vector of filepaths.
  * `perc`: percentage of "top hits" which should be used as a reference set in the next iteration. By default set to 0.05.
  * `rm_start`: whether to ignore the first codon of each sequence. Many organisms use alternative start codons such as TTG and CTG, which in other locations would generally code for leucine. There are a few approaches to deal with this. By default, `CUBScout` keeps each start codon and assigns it as though it were any other codon. Of course, this would slightly change leucine's contribution to codon usage bias. If you set `rm_start` to `true`, the first codon of every sequence is simply discarded. This will also affect the gene's length, which means it could be removed if it falls under the threshold. Other CUB packages (such as R's coRdon, alt.init = TRUE), assign all TTG and CTG codons to methionine, regardless of their location. I disagree with this approach from a biological perspective; those codons still code for leucine most of the time they are used. However, if you want matching output as you would get from coRdon, you can supply `ALTSTART_CodonDict` to the `dict` argument, and keep `rm_start` as `false`.
  * `rm_stop`: whether to remove stop codons from calculations of codon usage bias.
  * `threshold`: minimum length of a gene (in codons) to be used in codon usage bias calculations. By default this is set to 80 codons; any genes less than or equal to that length are discarded. If you want no genes discarded, set `threshold` to 0.

# Examples

```jldoctest
julia> ribosomal_genes = find_seqs(EXAMPLE_DATA_PATH, r"ribosomal"); # Get a vector which is true for ribosomal genes

julia> result = gcb(EXAMPLE_DATA_PATH); # Calculate GCB on example dataset

julia> round.(result.GCB[1:5], digits = 6)
5-element Vector{Float64}:
 -0.058765
 -0.08659
 -0.005496
 -0.065659
 -0.032062

julia> ribo_result = gcb(EXAMPLE_DATA_PATH, ref_vector = ribosomal_genes); # Calculate GCB with ribosomal genes as reference seed example dataset

julia> round.(ribo_result.GCB[1:5], digits = 6)
5-element Vector{Float64}:
 -0.135615
 -0.036687
 -0.169136
 -0.186104
 -0.01653

julia> gcb(EXAMPLE_DATA_PATH, ALTSTART_CodonDict); # Code TTG and CTG as methionine

julia> gcb(EXAMPLE_DATA_PATH, rm_start = true); # Remove start codons
```
