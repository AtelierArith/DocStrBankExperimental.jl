```
cai(sequences::Union{String, IO, FASTAReader, Vector{<:NucSeq}}, ref_vector::Vector{Bool}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{String}, Nothing} = nothing, rm_start = false, rm_stop = false, threshold = 80)
cai(sequences::Union{Vector{String}, Vector{<:IO}, Vector{<:FASTAReader}, Vector{<:Vector{<:NucSeq}}}, ref_vectors::Vector{Vector{Bool}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{Vector{String}}, Nothing} = nothing, rm_start = false, rm_stop = false, threshold = 80)
```

SharpとLiによるCAIの計算、1987年。

# 引数

  * `sequences`: 分析対象のDNAまたはRNA配列で、コーディング配列のみである必要があります。使用ケースに応じて、いくつかの形式を取ることができます。コーディング配列のfastaファイルへのパス（例：.fasta、.fna、.fa）や、これらのfastaファイルを指すIOまたはFASTAReaderであることができます。また、すでにJuliaの環境に持ち込んでいる場合は、BioSequencesのベクターであることもできます。品質チェックは行われないため、各エントリは個々のコーディング配列であり、正しいフレームで、5'または3'の非翻訳領域がないと仮定されます。複数のゲノム（または配列のセット）を分析している場合、`sequences`はファイルパス、IOStreams、FASTAReaders、または配列のベクターのベクターであり、各ベクターはゲノムに対応することができます。`CUBScout`はマルチスレッドであり、複数のスレッドが利用可能な場合、`CUBScout`は各ファイルパスにスレッドを割り当てます。そのため、ファイルパスのベクター（または`Vector{<:Vector{<:NucSeq}}`）を引数として提供する方が、パスのベクター全体にブロードキャストするよりも速くなります。単一のファイルは単一のスレッドによってのみアクセスされるため、分析されるファイルの総数よりも多くのスレッドを使用する価値はありません。
  * `ref_vector`: `cai`に必要な参照サブセット。fastaファイル内の配列の数と同じ長さの`Bool[]`で、参照サブセットとして使用したい配列には`true`、そうでない配列には`false`が含まれます。このベクターを生成するには`find_seqs()`を使用できます。複数のファイルパスを提供し、カスタム参照セットを希望する場合、`ref_vectors`はファイルパスのベクターに対応するベクターのベクターである必要があります。
  * `dict`: `CodonDict`型のコドン辞書。標準的な遺伝コードはデフォルトで読み込まれますが、必要に応じて`make_CodonDict`を使用して独自のコドン辞書を作成できます。
  * `names`: 各配列の名前のオプションのベクター。BioSequencesのベクターを提供する場合にのみ関連し、名前はfastaファイルから自動的に取得されます。`sequences`が`Vector{<:Vector{<:NucSeq}}`型の場合、`names`は`Vector{Vector{String}}`型である必要があります。
  * `rm_start`: 各配列の最初のコドンを無視するかどうか。多くの生物はTTGやCTGなどの代替開始コドンを使用しており、他の場所では一般的にロイシンをコードします。これに対処するためのいくつかのアプローチがあります。デフォルトでは、`CUBScout`は各開始コドンを保持し、他のコドンと同様に扱います。もちろん、これによりロイシンのコドン使用バイアスへの寄与がわずかに変わります。`rm_start`を`true`に設定すると、各配列の最初のコドンは単に破棄されます。これにより、遺伝子の長さにも影響を与え、しきい値を下回る場合は削除される可能性があります。他のCUBパッケージ（RのcoRdonなど、alt.init = TRUE）は、すべてのTTGおよびCTGコドンをメチオニンに割り当て、位置に関係なく扱います。このアプローチには生物学的な観点から異議を唱えます。これらのコドンは、使用されるほとんどの時間にロイシンをコードします。しかし、coRdonから得られる出力と一致させたい場合は、`dict`引数に`ALTSTART_CodonDict`を提供し、`rm_start`を`false`のままにすることができます。
  * `rm_stop`: コドン使用バイアスの計算からストップコドンを削除するかどうか。
  * `threshold`: コドン使用バイアスの計算に使用される遺伝子の最小長（コドン単位）。デフォルトでは80コドンに設定されており、その長さ以下の遺伝子は破棄されます。破棄される遺伝子がないようにしたい場合は、`threshold`を0に設定します。

# 例

```jldoctest
julia> ribosomal_genes = find_seqs(EXAMPLE_DATA_PATH, r"ribosomal"); # リボソーム遺伝子に対してtrueのベクターを取得

julia> result = cai(EXAMPLE_DATA_PATH, ribosomal_genes); # 例のデータセットでCAIを計算

julia> round.(result.CAI[1:5], digits = 6)
5-element Vector{Float64}:
 0.844967
 0.88548
 0.817348
 1.072675
 0.834179

julia> cai(EXAMPLE_DATA_PATH, ribosomal_genes, ALTSTART_CodonDict); # TTGとCTGをメチオニンとしてコード

julia> cai(EXAMPLE_DATA_PATH, ribosomal_genes, rm_start = true); # 開始コドンを削除
```
