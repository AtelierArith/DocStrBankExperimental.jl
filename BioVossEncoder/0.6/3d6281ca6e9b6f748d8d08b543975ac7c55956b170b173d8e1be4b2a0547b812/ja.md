```
vossmatrix(VossEncoder::VossEncoder{A, B}) where {A <: NucleicAcidAlphabet, B <: BitMatrix}
vossmatrix(seq::NucleicSeqOrView{A}) where {A <: NucleicAcidAlphabet}
vossmatrix(seq::SeqOrView{AminoAcidAlphabet}) where {A <: AminoAcidAlphabet}
```

与えられた核酸配列からバイナリシーケンス行列を作成します。

# 引数

  * `sequence`: 核酸配列。

# 戻り値

バイナリシーケンス行列。

# 例

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
