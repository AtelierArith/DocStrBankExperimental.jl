```
LongReads{A}(rdr::FASTQ.Reader, outfile::String, name::String, min_size::Integer) where {A<:DNAAlphabet}
```

FASTQファイルリーダーからロングリードデータストアを構築します。

# 引数

  * `rdr::FASTQ.Reader`: fastq形式のファイルのリーダー。
  * `outfile::String`: データストアのファイル名のプレフィックス。完全なファイル名には自動的に追加される「.loseq」拡張子が含まれます。
  * `name::String`: データストアのデフォルト名を示す文字列。データストアに名前を付けることは、下流のアプリケーションに役立ちます。
  * `min_size::Integer`: 最小リード長（塩基対単位）。データストアを構築する際に、リードシーケンスがこのカットオフよりも短い場合、そのリードは破棄されます。

# 例

```jldoctest
julia> using FASTX, ReadDatastores

julia> longrdr = open(FASTQ.Reader, "test/human_nanopore_tester_2D.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> ds = LongReads{DNAAlphabet{2}}(longrdr, "human-nanopore-tester", "nanopore-test", 0)
[ Info: FASTQファイルからロングリードデータストアを構築中
[ Info: データストアにロングリードを書き込み中
[ Info: ペアリードシーケンスをデータストアに書き込み完了
[ Info: シーケンスが短すぎるため、0リードが破棄されました
[ Info: データストアにインデックスを書き込み中
[ Info: 10リードを持つロングリードデータストアを構築しました
ロングリードデータストア 'nanopore-test': 10リード
```
