```
count_codons(path::AbstractString, remove_start::Bool = false, threshold::Integer = 0)
count_codons(stream::IO, remove_start::Bool = false, threshold::Integer = 0)
count_codons(reader::FASTAReader, remove_start::Bool = false, threshold::Integer = 0)
count_codons(sequences::Vector{<:NucSeq}, names::Vector{String} = String[], remove_start::Bool = false, threshold::Integer = 0)
count_codons(sequence::NucSeq, remove_start::Bool = false, threshold::Integer = 0)
```

Read a fasta file or BioSequence and return the occurence of each codon for each gene or sequence.

# Arguments

  * `path` or `stream` or `reader` or `sequence(s)`: Fasta sequence to analyze. This can be a path to a fasta file of sequences, an IOStream, an open FASTAReader, or a BioSequences nucleotide sequence, or a vector of nucleotide sequences. Note that count_codons isn't identifying ORFs - make sure these are actual CDSs in frame.
  * `remove_start`: Whether to ignore the initial start codon
  * `threshold`: Minimum length of the sequence *in codons* to be returned in the results.

# Output

If providing a single sequence, the result will be a 64x1 Matrix, which corresponds to the 64 codons in alphabetical order. If you want a list of the codons in alphabetical order, this is stored in `CUBScout.DEFAULT_CodonDict.codons`. If analyzing a fasta file or a vector of sequences, the result will be a tuple. The first element of the tuple is a 64xn matrix, where n = # of sequences above the threshold. The second element is a list of corresponding names for each column. The third element is a Boolean vector where `true` corresponds to sequences which did pass the threshold, and `false` is sequences which did not pass the threshold and so are not included in the results matrix. Names are pulled from fasta files and IO streams by default; if you would like to provide a vector of IDs or names when providing a `Vector{<:NucSeq}`, you can.

# Examples

```jldoctest
julia> using BioSequences: @dna_str

julia> example_dna = dna"ATGAAAATGAACTTTTGA"
18nt DNA Sequence:
ATGAAAATGAACTTTTGA

julia> count_codons(example_dna) |> first
1

julia> result = count_codons(EXAMPLE_DATA_PATH);

julia> first(result[1], 5)
5-element Vector{Int32}:
 32
  7
  6
 14
 11
```
