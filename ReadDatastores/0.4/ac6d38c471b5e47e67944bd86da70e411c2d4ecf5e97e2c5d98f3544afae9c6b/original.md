```
PairedReads{A}(rdrx::FASTQ.Reader, rdry::FASTQ.Reader, outfile::String, name::Union{String,Symbol}, minsize::Integer, maxsize::Integer, fragsize::Integer, orientation::PairedReadOrientation) where {A<:DNAAlphabet}
```

Construct a Paired Read Datastore from a pair of FASTQ file readers.

Paired-end sequencing reads typically come in the form of two FASTQ files, often named according to a convention `*_R1.fastq` and `*_R2.fastq`. One file contains all the "left" sequences of each pair, and the other contains all the "right" sequences of each pair. The first read pair is made of the first record in each file.

# Arguments

  * `rdrx::FASTQ.Reader`: The reader of the `*_R1.fastq` file.
  * `rdxy::FASTQ.Reader`: The reader of the `*_R2.fastq` file.
  * `outfile::String`: A prefix for the datastore's filename, the full filename will include a ".prseq" extension, which will be added automatically.
  * `name::String`: A string denoting a default name for your datastore. Naming datastores is useful for downstream applications.
  * `minsize::Integer`: A minimum read length (in base pairs). When building the datastore, if any pair of reads has one or both reads shorter than this cutoff, then the pair will be discarded.
  * `maxsize::Integer`: A maximum read length (in base pairs). When building the datastore, if any read has a greater length, it will be resized to this maximum length and added to the datastore.
  * `fragsize::Integer`: The average fragment length of the paired end library that was sequenced. This value is entirely optional, but may be important for downstream applications.
  * `orientation::PairedReadOrientation`: The orientation of the reads. Set it to `FwRv` for building a datastore from a sequenced paired end library, and set it to `RvFw` if you are building the datastore from reads sequenced from a long mate pair library.

# Examples

```jldoctest
julia> using FASTX, ReadDatastores

julia> fwq = open(FASTQ.Reader, "test/ecoli_tester_R1.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> rvq = open(FASTQ.Reader, "test/ecoli_tester_R2.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> ds = PairedReads{DNAAlphabet{2}}(fwq, rvq, "ecoli-test-paired", "my-ecoli-test", 250, 300, 0, FwRv)
[ Info: Building paired read datastore from FASTQ files
[ Info: Writing paired reads to datastore
[ Info: Done writing paired read sequences to datastore
[ Info: 0 read pairs were discarded due to a too short sequence
[ Info: 14 reads were truncated to 300 base pairs
[ Info: Created paired sequence datastore with 10 sequence pairs
Paired Read Datastore 'my-ecoli-test': 20 reads (10 pairs)

```
