```
count_codons(path::AbstractString, remove_start::Bool = false, threshold::Integer = 0)
count_codons(stream::IO, remove_start::Bool = false, threshold::Integer = 0)
count_codons(reader::FASTAReader, remove_start::Bool = false, threshold::Integer = 0)
count_codons(sequences::Vector{<:NucSeq}, names::Vector{String} = String[], remove_start::Bool = false, threshold::Integer = 0)
count_codons(sequence::NucSeq, remove_start::Bool = false, threshold::Integer = 0)
```

FASTAファイルまたはBioSequenceを読み込み、各遺伝子または配列の各コドンの出現回数を返します。

# 引数

  * `path`または`stream`または`reader`または`sequence(s)`：分析するFASTA配列。これは、配列のFASTAファイルへのパス、IOStream、オープンされたFASTAReader、またはBioSequencesのヌクレオチド配列、またはヌクレオチド配列のベクトルである可能性があります。count_codonsはORFを特定していないことに注意してください - これらが実際のCDSでフレーム内であることを確認してください。
  * `remove_start`：初期のスタートコドンを無視するかどうか
  * `threshold`：結果に返されるコドン単位の配列の最小長さ。

# 出力

単一の配列を提供する場合、結果は64x1の行列となり、これはアルファベット順の64のコドンに対応します。アルファベット順のコドンのリストが必要な場合、これは`CUBScout.DEFAULT_CodonDict.codons`に格納されています。FASTAファイルまたは配列のベクトルを分析する場合、結果はタプルになります。タプルの最初の要素は64xnの行列で、ここでnは閾値を超える配列の数です。タプルの第二要素は各列に対応する名前のリストです。第三要素はブールベクトルで、`true`は閾値を超えた配列に対応し、`false`は閾値を超えなかった配列に対応し、結果の行列には含まれません。名前はデフォルトでFASTAファイルとIOストリームから取得されます。`Vector{<:NucSeq}`を提供する際にIDまたは名前のベクトルを提供したい場合は、可能です。

# 例

```jldoctest
julia> using BioSequences: @dna_str

julia> example_dna = dna"ATGAAAATGAACTTTTGA"
18nt DNA Sequence:
ATGAAAATGAACTTTTGA

julia> count_codons(example_dna) |> first
1

julia> result = count_codons(EXAMPLE_DATA_PATH);

julia> first(result[1], 5)
5-element Vector{Int32}:
 32
  7
  6
 14
 11
```
