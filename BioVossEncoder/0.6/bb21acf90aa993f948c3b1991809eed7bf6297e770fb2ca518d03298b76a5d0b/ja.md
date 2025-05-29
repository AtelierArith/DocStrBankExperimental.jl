```
vossvector(seq::NucleicSeqOrView{A}, molecule::T) where {A <: NucleicAcidAlphabet, T <: BioSymbol}
vossvector(seq::SeqOrView{AminoAcidAlphabet}, molecule::T) where {T <: BioSymbol}
vossvector(seq::SeqOrView{A}, molecules::Tuple{Vararg{T}}) where {A <: Alphabet, T <: BioSymbol}
```

ヌクレオチドの配列をバイナリ表現に変換します。

# 引数

  * `seq::SeqOrView{A}`: 入力されるヌクレオチドの配列。
  * `molecule::BioSymbol`: 1としてエンコードされるヌクレオチド、他は0としてエンコードされます。
  * `molecules::Tuple{Vararg{T}}`: 1としてエンコードされるヌクレオチド、他は0としてエンコードされます。

# 戻り値

入力された配列のバイナリエンコーディングを表す`BitVector`。ここで、1は指定されたヌクレオチドの存在を示し、0は配列のi番目の位置における不在を示します。

# 例

```julia
julia> vossvector(dna"ACGT", DNA_A)

    4-element view(::BitMatrix, 1, :) with eltype Bool:
     1
     0
     0
     0
```
