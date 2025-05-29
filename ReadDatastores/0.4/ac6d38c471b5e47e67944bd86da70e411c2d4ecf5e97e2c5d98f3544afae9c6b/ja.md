```
PairedReads{A}(rdrx::FASTQ.Reader, rdry::FASTQ.Reader, outfile::String, name::Union{String,Symbol}, minsize::Integer, maxsize::Integer, fragsize::Integer, orientation::PairedReadOrientation) where {A<:DNAAlphabet}
```

ペアリードデータストアを一対のFASTQファイルリーダーから構築します。

ペアエンドシーケンシングリードは通常、2つのFASTQファイルの形で提供され、一般的に`*_R1.fastq`と`*_R2.fastq`という命名規則に従います。1つのファイルには各ペアのすべての「左」シーケンスが含まれ、もう1つのファイルには各ペアのすべての「右」シーケンスが含まれます。最初のリードペアは、各ファイルの最初のレコードで構成されます。

# 引数

  * `rdrx::FASTQ.Reader`: `*_R1.fastq`ファイルのリーダー。
  * `rdxy::FASTQ.Reader`: `*_R2.fastq`ファイルのリーダー。
  * `outfile::String`: データストアのファイル名のプレフィックス。完全なファイル名には自動的に追加される".prseq"拡張子が含まれます。
  * `name::String`: データストアのデフォルト名を示す文字列。データストアに名前を付けることは、下流のアプリケーションに役立ちます。
  * `minsize::Integer`: 最小リード長（塩基対単位）。データストアを構築する際に、リードのペアのいずれかがこのカットオフよりも短い場合、そのペアは破棄されます。
  * `maxsize::Integer`: 最大リード長（塩基対単位）。データストアを構築する際に、いずれかのリードがこの最大長よりも長い場合、そのリードはこの最大長にリサイズされ、データストアに追加されます。
  * `fragsize::Integer`: シーケンスされたペアエンドライブラリの平均フラグメント長。この値は完全にオプションですが、下流のアプリケーションにとって重要な場合があります。
  * `orientation::PairedReadOrientation`: リードの向き。シーケンスされたペアエンドライブラリからデータストアを構築する場合は`FwRv`に設定し、ロングメイトペアライブラリからシーケンスされたリードからデータストアを構築する場合は`RvFw`に設定します。

# 例

```jldoctest
julia> using FASTX, ReadDatastores

julia> fwq = open(FASTQ.Reader, "test/ecoli_tester_R1.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> rvq = open(FASTQ.Reader, "test/ecoli_tester_R2.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> ds = PairedReads{DNAAlphabet{2}}(fwq, rvq, "ecoli-test-paired", "my-ecoli-test", 250, 300, 0, FwRv)
[ Info: FASTQファイルからペアリードデータストアを構築中
[ Info: データストアにペアリードを書き込み中
[ Info: ペアリードシーケンスのデータストアへの書き込みが完了しました
[ Info: シーケンスが短すぎるため、0リードペアが破棄されました
[ Info: 14リードが300塩基対に切り詰められました
[ Info: 10シーケンスペアを持つペアシーケンスデータストアが作成されました
ペアリードデータストア 'my-ecoli-test': 20リード（10ペア）

```
