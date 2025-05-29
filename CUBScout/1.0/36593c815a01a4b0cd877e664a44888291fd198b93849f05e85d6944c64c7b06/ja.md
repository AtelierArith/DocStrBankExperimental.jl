```
gcb(sequences::Union{String, IO, FASTAReader, Vector{<:NucSeq}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{String}, Nothing} = nothing, ref_vector = [], perc = 0.05, rm_start = false, rm_stop = false, threshold = 80)
gcb(sequences::Union{Vector{String}, Vector{<:IO}, Vector{<:FASTAReader}, Vector{<:Vector{<:NucSeq}}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{Vector{String}}, Nothing} = nothing, ref_vectors = [], perc = 0.05, rm_start = false, rm_stop = false, threshold = 80)
```

Merkl, 2003からGCBを計算します。

# 引数

  * `sequences`: 分析されるDNAまたはRNA配列で、コーディング配列のみである必要があります。これは、使用ケースに応じてさまざまな形式を取ることができます。コーディング配列のfastaファイルへのパス（例：.fasta、.fna、.fa）や、これらのfastaファイルを指すIOまたはFASTAReaderであることができます。また、すでにJuliaの環境に持ち込んでいる場合は、BioSequencesのベクターであることもできます。品質チェックは行われないため、各エントリは個々のコーディング配列であり、正しいフレームで、5'または3'の非翻訳領域がないと仮定されます。複数のゲノム（または配列のセット）を分析している場合、`sequences`はファイルパス、IOStreams、FASTAReaders、またはBioSequencesのベクターのベクターであり、各ベクターはゲノムに対応することができます。`CUBScout`はマルチスレッドであり、複数のスレッドが利用可能な場合、`CUBScout`は各fastaファイルまたはBioSequencesのベクターにスレッドを割り当てます。そのため、引数としてファイルパスのベクター（または`Vector{<:Vector{<:NucSeq}}`）を提供する方が、パスのベクターに対してブロードキャストするよりも速くなります。単一のファイルは単一のスレッドによってのみアクセスされるため、分析されるファイルの総数よりも多くのスレッドを使用する価値はありません。
  * `dict`: `CodonDict`型のコドン辞書。標準遺伝コードはデフォルトで読み込まれますが、必要に応じて`make_CodonDict`を使用して独自のコドン辞書を作成できます。
  * `names`: 各配列の名前のオプションのベクター。BioSequencesのベクターを提供する場合にのみ関連し、名前はfastaファイルから自動的に取得されます。`sequences`が`Vector{<:Vector{<:NucSeq}}`型の場合、`names`は`Vector{Vector{String}}`型である必要があります。
  * `ref_vector`: オプションの参照サブセット。デフォルトではgcbはすべての遺伝子をシードとして計算を開始します。カスタム参照セットを提供したい場合、それはfastaファイル内の配列の数と同じ長さの`Bool[]`のベクターであり、参照サブセットとして使用したい配列には`true`、使用したくない配列には`false`を含む必要があります。このベクターを生成するには`find_seqs()`を使用できます。複数のファイルパスを提供し、カスタム参照セットを希望する場合、`ref_vectors`はファイルパスのベクターに対応するベクターのベクターである必要があります。
  * `perc`: 次の反復で参照セットとして使用されるべき「トップヒット」の割合。デフォルトは0.05に設定されています。
  * `rm_start`: 各配列の最初のコドンを無視するかどうか。多くの生物はTTGやCTGなどの代替開始コドンを使用しており、他の場所では一般的にロイシンをコードします。これに対処するためのいくつかのアプローチがあります。デフォルトでは、`CUBScout`は各開始コドンを保持し、他のコドンと同様に扱います。もちろん、これによりロイシンのコドン使用バイアスへの寄与がわずかに変わります。`rm_start`を`true`に設定すると、各配列の最初のコドンは単に破棄されます。これにより遺伝子の長さにも影響を与え、しきい値を下回る場合は削除される可能性があります。他のCUBパッケージ（RのcoRdonなど）は、すべてのTTGおよびCTGコドンをメチオニンに割り当て、位置に関係なく処理します。このアプローチには生物学的な観点から異議を唱えます。これらのコドンは、使用されるほとんどの時間にロイシンをコードします。しかし、coRdonから得られる出力と一致させたい場合は、`dict`引数に`ALTSTART_CodonDict`を提供し、`rm_start`を`false`のままにすることができます。
  * `rm_stop`: コドン使用バイアスの計算からストップコドンを削除するかどうか。
  * `threshold`: コドン使用バイアスの計算に使用される遺伝子の最小長（コドン単位）。デフォルトは80コドンに設定されており、その長さ以下の遺伝子は破棄されます。遺伝子を破棄したくない場合は、`threshold`を0に設定します。

# 例

```jldoctest
julia> ribosomal_genes = find_seqs(EXAMPLE_DATA_PATH, r"ribosomal"); # リボソーム遺伝子に対してtrueのベクターを取得

julia> result = gcb(EXAMPLE_DATA_PATH); # 例のデータセットでGCBを計算

julia> round.(result.GCB[1:5], digits = 6)
5-element Vector{Float64}:
 -0.058765
 -0.08659
 -0.005496
 -0.065659
 -0.032062

julia> ribo_result = gcb(EXAMPLE_DATA_PATH, ref_vector = ribosomal_genes); # リボソーム遺伝子を参照シードとして例のデータセットでGCBを計算

julia> round.(ribo_result.GCB[1:5], digits = 6)
5-element Vector{Float64}:
 -0.135615
 -0.036687
 -0.169136
 -0.186104
 -0.01653

julia> gcb(EXAMPLE_DATA_PATH, ALTSTART_CodonDict); # TTGとCTGをメチオニンとしてコード

julia> gcb(EXAMPLE_DATA_PATH, rm_start = true); # 開始コドンを削除
```
