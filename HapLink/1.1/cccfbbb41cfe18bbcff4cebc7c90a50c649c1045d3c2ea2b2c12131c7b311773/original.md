```
consensus_record(
    reference::Union{AbstractString,AbstractPath},
    variants::Union{AbstractString,AbstractPath};
    frequency::Float64=0.5,
    prefix::Union{AbstractString,Nothing}=nothing,
)
```

Get the consensus `FASTA.Record`from `variants` applied to the first sequence in `reference`.

# Arguments

  * `reference::Union{AbstractString,AbstractPath}`: Path to the reference genome that variants were called from. Only the first sequence will be used.
  * `variants::Union{AbstractString,AbstractPath}`: Path to variant call file that mutations will be applied from

# Keywords

  * `frequency::Float64=0.5`: Fraction of total reads that must have supported the alternate position in order to be included as part of the consensus. In other words, only VCF records that have a `AF` (allele/alternate frequency) higher than this will be considered to contribute to the consensus.
  * `prefix::Union{AbstractString,Nothing}=nothing`: Name to give to the output record. By default, the name of the output record will be the same as the name of the input record with `_CONSENSUS` appended. If `prefix` is supplied, then the name of the output record will be `$(prefix)_CONSENSUS`.
