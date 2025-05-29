```
mcb(sequences::Union{String, IO, FASTAReader, Vector{<:NucSeq}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{String}, Nothing} = nothing, ref_seqs = (), rm_start = false, rm_stop = false, threshold = 80)
mcb(sequences::Union{Vector{String}, Vector{<:IO}, Vector{<:FASTAReader}, Vector{<:Vector{<:NucSeq}}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{Vector{String}}, Nothing} = nothing, ref_seqs = (), rm_start = false, rm_stop = false, threshold = 80)
```

UrrutiaとHurstによるMCBを計算します（2001年）。

# 引数

  * `sequences`: 分析されるDNAまたはRNA配列で、コーディング配列のみである必要があります。使用ケースに応じて、いくつかの形式を取ることができます。コーディング配列のfastaファイルへのパス（例：.fasta、.fna、.fa）や、これらのfastaファイルを指すIOまたはFASTAReaderであることができます。また、すでにJuliaの環境に持ち込んでいる場合は、BioSequencesのベクターであることもできます。品質チェックは行われないため、各エントリは個々のコーディング配列であり、正しいフレームであり、5'または3'の非翻訳領域がないと仮定されます。複数のゲノム（または配列のセット）を分析している場合、`sequences`はファイルパス、IOStreams、FASTAReaders、または配列のベクターのベクターであることができ、各ベクターはゲノムに対応します。`CUBScout`はマルチスレッドであり、複数のスレッドが利用可能な場合、`CUBScout`は各ファイルパスにスレッドを割り当てます。そのため、ファイルパスのベクター（または`Vector{<:Vector{<:NucSeq}}`）を引数として提供する方が、パスのベクター全体にブロードキャストするよりも速くなります。単一のファイルは単一のスレッドによってのみアクセスされるため、分析されるファイルの総数よりも多くのスレッドを使用する価値はありません。
  * `dict`: `CodonDict`型のコドン辞書。標準的な遺伝コードはデフォルトで読み込まれますが、必要に応じて`make_CodonDict`を使用して独自のコドン辞書を作成できます。
  * `names`: 各配列の名前のオプションのベクター。BioSequencesのベクターを提供する場合にのみ関連し、名前はfastaファイルから自動的に取得されます。`sequences`が`Vector{<:Vector{<:NucSeq}}`型の場合、`names`は`Vector{Vector{String}}`型である必要があります。
  * `ref_seqs`: デフォルトでは、各遺伝子のコドン使用バイアスは、全ゲノム（「自己」）を参照サブセットとして使用して計算されます。リボソーム遺伝子など、計算に対して独自のサブセットを指定したい場合、`ref_seqs`は`("subset_name" = Bool[],)`の形式の名前付きタプルを取ります。ここで、`Bool[]`はfastaファイル内の配列の数と同じ長さであり、参照サブセットとして使用したい配列には`true`、使用したくない配列には`false`が含まれます。このベクターを生成するには`find_seqs()`を使用できます。複数の参照サブセットを名前付きタプルの別々のエントリとして提供でき、`CUBScout`は各サブセットを使用して計算された測定値を返します。複数の配列セットを提供し、カスタム参照セットを希望する場合、`ref_seqs`は配列のベクターに対応する名前付きタプルのベクターである必要があります。
  * `rm_start`: 各配列の最初のコドンを無視するかどうか。多くの生物はTTGやCTGなどの代替開始コドンを使用しており、他の場所では一般的にロイシンをコードします。これに対処するためのいくつかのアプローチがあります。デフォルトでは、`CUBScout`は各開始コドンを保持し、他のコドンと同様に扱います。もちろん、これによりロイシンのコドン使用バイアスへの寄与がわずかに変わります。`rm_start`を`true`に設定すると、すべての配列の最初のコドンは単に破棄されます。これにより、遺伝子の長さにも影響を与え、しきい値を下回る場合は削除される可能性があります。他のCUBパッケージ（RのcoRdonなど、alt.init = TRUE）は、位置に関係なくすべてのTTGおよびCTGコドンをメチオニンに割り当てます。このアプローチには生物学的な観点から異議を唱えます。これらのコドンは、使用されるほとんどの時間ロイシンをコードします。しかし、coRdonから得られる出力と一致させたい場合は、`dict`引数に`ALTSTART_CodonDict`を提供し、`rm_start`を`false`のままにすることができます。
  * `rm_stop`: コドン使用バイアスの計算からストップコドンを削除するかどうか。
  * `threshold`: コドン使用バイアスの計算に使用される遺伝子の最小長（コドン単位）。デフォルトでは80コドンに設定されており、その長さ以下の遺伝子は破棄されます。破棄される遺伝子がないようにしたい場合は、`threshold`を0に設定します。

# 例

```jldoctest
julia> result = mcb(EXAMPLE_DATA_PATH); # 例のデータセットで測定を計算

julia> result_300 = mcb(EXAMPLE_DATA_PATH, threshold = 300); # しきい値の長さを増加

julia> length(result.self)
3801

julia> length(result_300.self)
1650

julia> round.(result.self[1:5], digits = 6)
5-element Vector{Float64}:
 0.087211
 0.178337
 0.189682
 0.24012
 0.149869

julia> mcb(EXAMPLE_DATA_PATH, ALTSTART_CodonDict); # TTGとCTGをメチオニンとしてコード

julia> mcb(EXAMPLE_DATA_PATH, rm_start = true); # 開始コドンを削除

julia> all_genes = find_seqs(EXAMPLE_DATA_PATH, r""); # すべての遺伝子に対してtrueのベクターを取得

julia> ribosomal_genes = find_seqs(EXAMPLE_DATA_PATH, r"ribosomal"); # リボソーム遺伝子に対してtrueのベクターを取得

julia> mcb(EXAMPLE_DATA_PATH, ref_seqs = (ribosomal = ribosomal_genes,)); # リボソーム遺伝子を参照サブセットとして使用して計算

julia> mcb(EXAMPLE_DATA_PATH, ref_seqs = (self = all_genes, ribosomal = ribosomal_genes,)); # すべての遺伝子とリボソーム遺伝子を参照サブセットとして使用して計算
```
