```
LongReads{A}(rdr::FASTQ.Reader, outfile::String, name::String, min_size::Integer) where {A<:DNAAlphabet}
```

Construct a Long Read Datastore from a FASTQ file reader.

# Arguments

  * `rdr::FASTQ.Reader`: The reader of the fastq formatted file.
  * `outfile::String`: A prefix for the datastore's filename, the full filename will include a ".loseq" extension, which will be added automatically.
  * `name::String`: A string denoting a default name for your datastore. Naming datastores is useful for downstream applications.
  * `min_size::Integer`: A minimum read length (in base pairs). When building the datastore, if any read sequence is shorter than this cutoff, then the read will be discarded.

# Examples

```jldoctest
julia> using FASTX, ReadDatastores

julia> longrdr = open(FASTQ.Reader, "test/human_nanopore_tester_2D.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> ds = LongReads{DNAAlphabet{2}}(longrdr, "human-nanopore-tester", "nanopore-test", 0)
[ Info: Building long read datastore from FASTQ file
[ Info: Writing long reads to datastore
[ Info: Done writing paired read sequences to datastore
[ Info: 0 reads were discarded due to a too short sequence
[ Info: Writing index to datastore
[ Info: Built long read datastore with 10 reads
Long Read Datastore 'nanopore-test': 10 reads

```
