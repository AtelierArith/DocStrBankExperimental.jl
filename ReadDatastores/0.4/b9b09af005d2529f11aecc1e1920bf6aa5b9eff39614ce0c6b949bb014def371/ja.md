```
LinkedReads{A}(fwq::FASTQ.Reader, rvq::FASTQ.Reader, outfile::String, name::String, format::LinkedReadsFormat, max_read_len::Integer, chunksize::Int = 1000000) where {A<:DNAAlphabet}
```

ペアのFASTQファイルリーダーからLinked Readデータストアを構築します。

ペアシーケンシングリードは通常、2つのFASTQファイルの形で提供され、一般的に`*_R1.fastq`と`*_R2.fastq`という命名規則に従います。1つのファイルには各ペアのすべての「左」シーケンスが含まれ、もう1つのファイルには各ペアのすべての「右」シーケンスが含まれます。最初のリードペアは、各ファイルの最初のレコードで構成されます。

# 引数

  * `rdrx::FASTQ.Reader`: `*_R1.fastq`ファイルのリーダー。
  * `rdxy::FASTQ.Reader`: `*_R2.fastq`ファイルのリーダー。
  * `outfile::String`: データストアのファイル名のプレフィックス。完全なファイル名には自動的に追加される".prseq"拡張子が含まれます。
  * `name::String`: データストアのデフォルト名を示す文字列。データストアに名前を付けることは、下流のアプリケーションに役立ちます。
  * `format::LinkedReadsFormat`: FASTQファイルのリンクされたリード形式を指定します。プレーンな10xファイルがある場合は、formatを`Raw10x`に設定します。UCDavis形式で出力された10xリードがある場合は、formatを`UCDavis10x`に設定します。
  * `chunksize::Int = 1000000`: タグソートステップ中にディスクバッチごとに処理するリードペアの数。

# 例

```jldoctest
julia> using FASTX, ReadDatastores

julia> fqa = open(FASTQ.Reader, "test/10x_tester_R1.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> fqb = open(FASTQ.Reader, "test/10x_tester_R2.fastq")
FASTX.FASTQ.Reader{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(BioGenerics.Automa.State{TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}}(TranscodingStreams.TranscodingStream{TranscodingStreams.Noop,IOStream}(<mode=idle>), 1, 1, false), nothing)

julia> ds = LinkedReads{DNAAlphabet{2s}}(fqa, fqb, "10xtest", "ucdavis-test", UCDavis10x, 250)
[ Info: 1000000ペアのタグソートチャンクを構築中
[ Info: チャンク0に83のタグソートされたリードペアをダンプ中
[ Info: ダンプ完了
[ Info: これまでに83のリードペアを処理しました
[ Info: タグソートチャンクの構築が完了しました
[ Info: ディスクからのマージを実行中
[ Info: 83のread_tagエントリのためのスペースを確保中
[ Info: チャンク0が完了しました
[ Info: ディスクからのマージが完了しました
[ Info: 83のread tagエントリを書き込み中
[ Info: 83のシーケンスペアを持つリンクされたシーケンスデータストアを作成しました
Linked Read Datastore 'ucdavis-test': 166 reads (83 pairs)

```
