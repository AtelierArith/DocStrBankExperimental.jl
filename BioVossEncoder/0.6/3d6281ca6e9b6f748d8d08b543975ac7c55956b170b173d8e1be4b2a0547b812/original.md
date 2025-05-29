```
vossmatrix(VossEncoder::VossEncoder{A, B}) where {A <: NucleicAcidAlphabet, B <: BitMatrix}
vossmatrix(seq::NucleicSeqOrView{A}) where {A <: NucleicAcidAlphabet}
vossmatrix(seq::SeqOrView{AminoAcidAlphabet}) where {A <: AminoAcidAlphabet}
```

Create a binary sequence matrix from a given nucleic acid sequence.

# Arguments

  * `sequence`: A nucleic acid sequence.

# Returns

The binary sequence matrix.

# Examples

```julia
julia> vossmatrix(aa"IANRMWRDTIED")

    20×12 BitMatrix:
    0  1  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  1  0  0  0  1
    0  0  0  0  0  0  0  0  0  0  1  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    1  0  0  0  0  0  0  0  0  1  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  1  0  0  0  0  0  0  0
    0  0  1  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  1  0  0  1  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  1  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
    0  0  0  0  0  1  0  0  0  0  0  0
    0  0  0  0  0  0  0  0  0  0  0  0
```
