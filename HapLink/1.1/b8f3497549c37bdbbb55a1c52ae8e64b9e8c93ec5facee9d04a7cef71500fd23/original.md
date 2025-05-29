```
consensus_haplotype(
    reference::NucleotideSeq,
    variants::Union{AbstractString,AbstractPath};
    frequency::Float64=0.5,
)
```

Get the consensus `Haplotype`from `variants` applied to `reference`.

# Arguments

  * `reference::NucleotideSeq`: Sequence of the reference genome that variants were called from
  * `variants::Union{AbstractString,AbstractPath}`: Path to variant call file that mutations will be applied from

# Keywords

  * `frequency::Float64=0.5`: Fraction of total reads that must have supported the alternate position in order to be included as part of the consensus. In other words, only VCF records that have a `AF` (allele/alternate frequency) higher than this will be considered to contribute to the consensus.
