```
enc(sequences::Union{String, IO, FASTAReader, Vector{<:NucSeq}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{String}, Nothing} = nothing, rm_start = false, rm_stop = false, threshold = 80)
enc(sequences::Union{Vector{String}, Vector{<:IO}, Vector{<:FASTAReader}, Vector{<:Vector{<:NucSeq}}}, dict::CodonDict = DEFAULT_CodonDict; names::Union{Vector{Vector{String}}, Nothing} = nothing, rm_start = false, rm_stop = false, threshold = 80)
```

Wright, 1990 による ENC を計算します。  

# 引数

  * `sequences`: 分析対象の DNA または RNA 配列で、コーディング配列のみである必要があります。使用ケースに応じて、いくつかの形式を取ることができます。コーディング配列の fasta ファイルへのパス（例: .fasta, .fna, .fa）や、これらの fasta ファイルを指す IO または FASTAReader であることができます。また、すでに Julia の環境に取り込んでいる場合は、BioSequences のベクターであることもできます。品質チェックは行われないため、各エントリは個々のコーディング配列であり、正しいフレームで、5' または 3' 非翻訳領域がないと仮定されます。複数のゲノム（または配列のセット）を分析している場合、`sequences` はファイルパス、IOStreams、FASTAReaders、または配列のベクターのベクターであることができ、各ベクターはゲノムに対応します。`CUBScout` はマルチスレッドであり、利用可能なスレッドが複数ある場合、`CUBScout` は各ファイルパスにスレッドを割り当てます。そのため、ファイルパスのベクター（または `Vector{<:Vector{<:NucSeq}}`）を引数として提供する方が、パスのベクター全体にブロードキャストするよりも速くなります。単一のファイルは単一のスレッドによってのみアクセスされるため、分析されるファイルの総数よりも多くのスレッドを使用する価値はありません。
  * `dict`: `CodonDict` 型のコドン辞書。標準の遺伝コードはデフォルトで読み込まれますが、必要に応じて `make_CodonDict` を使用して独自のコドン辞書を作成できます。
  * `names`: 各配列の名前のオプションのベクター。BioSequences のベクターを提供する場合にのみ関連し、名前は fasta ファイルから自動的に取得されます。`sequences` が `Vector{<:Vector{<:NucSeq}}` 型の場合、`names` は `Vector{Vector{String}}` 型である必要があります。
  * `rm_start`: 各配列の最初のコドンを無視するかどうか。多くの生物は TTG や CTG などの代替開始コドンを使用しており、他の場所では一般的にロイシンをコードします。これに対処するためのいくつかのアプローチがあります。デフォルトでは、`CUBScout` は各開始コドンを保持し、他のコドンと同様に扱います。もちろん、これによりロイシンのコドン使用バイアスへの寄与がわずかに変わります。`rm_start` を `true` に設定すると、すべての配列の最初のコドンは単純に破棄されます。これにより、遺伝子の長さにも影響があり、しきい値を下回る場合は削除される可能性があります。他の CUB パッケージ（R の coRdon など、alt.init = TRUE）では、すべての TTG および CTG コドンをメチオニンに割り当てますが、その位置に関係なく割り当てます。このアプローチには生物学的な観点から異議を唱えます。これらのコドンは、使用されるほとんどの時間にロイシンをコードします。ただし、coRdon から得られる出力と一致させたい場合は、`dict` 引数に `ALTSTART_CodonDict` を提供し、`rm_start` を `false` のままにすることができます。
  * `rm_stop`: コドン使用バイアスの計算からストップコドンを削除するかどうか。
  * `threshold`: コドン使用バイアスの計算に使用される遺伝子の最小長（コドン単位）。デフォルトでは 80 コドンに設定されており、その長さ以下の遺伝子は破棄されます。破棄される遺伝子がないようにしたい場合は、`threshold` を 0 に設定します。

# 例

```jldoctest
julia> result = enc(EXAMPLE_DATA_PATH); # 例のデータセットで ENC を実行

julia> round.(result.ENC[1:5], digits = 6)
5-element Vector{Float64}:
 56.787282
 52.725947
 59.287949
 52.296686
 55.262981

julia> result_300 = enc(EXAMPLE_DATA_PATH, threshold = 300); # しきい値の長さを増加

julia> length(result.ENC)
3801

julia> length(result_300.ENC)
1650

julia> enc(EXAMPLE_DATA_PATH, ALTSTART_CodonDict); # TTG と CTG をメチオニンとしてコード

julia> enc(EXAMPLE_DATA_PATH, rm_start = true); # 開始コドンを削除
```
