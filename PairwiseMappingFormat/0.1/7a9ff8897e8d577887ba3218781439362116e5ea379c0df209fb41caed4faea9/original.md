```
PAFRecord(buffer_size::Int)
```

Mutable type representing a single PAF line. The content of the record is accessed through its properties.

# Examples

```jldoctest
julia> record = PAFReader(first, open(path_to_paf));

julia> record.qname
"query1"

julia> record.qlen
301156
```

See also: [`PAFReader`](@ref)

# Extended help

The following properties may be used:

  * `qname::StringView`. The query name, May be empty, and contain any bytes except `\t` and `\n`.
  * `tname::Union{StringView, Nothing}`. Target name. Like `qname`, but is `nothing` if and only if the record is unmapped.
  * `qlen` and `tlen::Int`, and gives the length of the query and target sequences, respectively. This must be > 0.
  * `qstart`, `qend`, `tstart` and `tend::Int`, and give the starting and ending positions of the alignments on the query and target strand. These uses one-based, closed interval indexing as usual in Julia, but unlike the underlying PAF format. The ending positions are always >= the starting ones, and the ending positions are always <= the query/target lengths.
  * `matches::Int` gives the number of nucleotides / residues which match (i.e. are equal) in the alignment.
  * `alnlen::Int` gives the length of the alignment
  * `mapq::Union{Int, Nothing}` gives the mapping quality, or `nothing` if  this information is unavailable.
  * `is_rc::Union{Bool,Nothing}` tells if the query and target strands are reverse-complement relative to each other. Is `nothing` if the record is unmapped.
