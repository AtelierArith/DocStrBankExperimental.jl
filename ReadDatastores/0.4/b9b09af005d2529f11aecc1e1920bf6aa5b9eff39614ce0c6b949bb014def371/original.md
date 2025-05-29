```
LinkedReads{A}(fwq::FASTQ.Reader, rvq::FASTQ.Reader, outfile::String, name::String, format::LinkedReadsFormat, max_read_len::Integer, chunksize::Int = 1000000) where {A<:DNAAlphabet}
```

Construct a Linked Read Datastore from a pair of FASTQ file readers.

Paired sequencing reads typically come in the form of two FASTQ files, often named according to a convention `*_R1.fastq` and `*_R2.fastq`. One file contains all the "left" sequences of each pair, and the other contains all the "right" sequences of each pair. The first read pair is made of the first record in each file.

# Arguments

  * `rdrx::FASTQ.Reader`: The reader of the `*_R1.fastq` file.
  * `rdxy::FASTQ.Reader`: The reader of the `*_R2.fastq` file.
  * `outfile::String`: A prefix for the datastore's filename, the full filename will include a ".prseq" extension, which will be added automatically.
  * `name::String`: A string denoting a default name for your datastore. Naming datastores is useful for downstream applications.
  * `format::LinkedReadsFormat`: Specify the linked reads format of your fastq files. If you have plain 10x files, set format to `Raw10x`. If you have 10x reads output in the UCDavis format, set the format to `UCDavis10x`.
  * `chunksize::Int = 1000000`: How many read pairs to process per disk batch during the tag sorting step of construction.

# Examples

```jldoctest
julia> using FASTX, ReadDatastores

julia> fqa = open(FASTQ.Reader, "test/10x_tester_R1.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> fqb = open(FASTQ.Reader, "test/10x_tester_R2.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> ds = LinkedReads{DNAAlphabet{2s}}(fqa, fqb, "10xtest", "ucdavis-test", UCDavis10x, 250)
[ Info: Building tag sorted chunks of 1000000 pairs
[ Info: Dumping 83 tag-sorted read pairs to chunk 0
[ Info: Dumped
[ Info: Processed 83 read pairs so far
[ Info: Finished building tag sorted chunks
[ Info: Performing merge from disk
[ Info: Leaving space for 83 read_tag entries
[ Info: Chunk 0 is finished
[ Info: Finished merge from disk
[ Info: Writing 83 read tag entries
[ Info: Created linked sequence datastore with 83 sequence pairs
Linked Read Datastore 'ucdavis-test': 166 reads (83 pairs)

```
