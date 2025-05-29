```
vossvector(seq::NucleicSeqOrView{A}, molecule::T) where {A <: NucleicAcidAlphabet, T <: BioSymbol}
vossvector(seq::SeqOrView{AminoAcidAlphabet}, molecule::T) where {T <: BioSymbol}
vossvector(seq::SeqOrView{A}, molecules::Tuple{Vararg{T}}) where {A <: Alphabet, T <: BioSymbol}
```

Converts a sequence of nucleotides into a binary representation.

# Arguments

  * `seq::SeqOrView{A}`: The input sequence of nucleotides.
  * `molecule::BioSymbol`: The nucleotide to be encoded as 1, while others are encoded as 0.
  * `molecules::Tuple{Vararg{T}}`: The nucleotides to be encoded as 1, while others are encoded as 0.

# Returns

A `BitVector` representing the binary encoding of the input sequence, where 1 indicates the presence of the specified nucleotide and 0 indicates the absence in the ith position of the sequence.

# Examples

```julia
julia> vossvector(dna"ACGT", DNA_A)

    4-element view(::BitMatrix, 1, :) with eltype Bool:
     1
     0
     0
     0
```
