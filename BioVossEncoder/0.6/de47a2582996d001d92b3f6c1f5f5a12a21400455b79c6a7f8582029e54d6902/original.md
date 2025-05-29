```
struct VossEncoder{A<:NucleicAcidAlphabet, B<:BitMatrix}
```

The `VossEncoder` struct represents a binary matrix encoding a sequence of nucleic acids. This is also called the Voss representation of a sequence.

# Fields

  * `alphabet::A`: The nucleic acid alphabet used for encoding.
  * `bitmatrix::B`: The binary matrix representing the encoded sequence.

# Constructors

  * `VossEncoder(sequence::SeqOrView{A})`: Constructs a `VossEncoder` from a sequence of nucleic acids.

## Arguments

  * `sequence::SeqOrView{A}`: The sequence of nucleic acids to be encoded.
