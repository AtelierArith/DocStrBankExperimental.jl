```
codon_frequency(codon_counts::Matrix{<:Integer}, form::String, dict::CodonDict = DEFAULT_CodonDict)
```

コドンカウントの行列からコドン頻度を計算します。最初の引数として `Matrix{<:Integer}` を受け取り、これは `count_codons()` の結果です。`form` は次の4つのオプションのいずれかです: -`net_genomic`: 全ゲノムにわたる各コドンの頻度（行列）。 -`net_gene`: 各遺伝子内の各コドンの頻度（列）。 -`byAA_genomic`: 全ゲノムにわたる各アミノ酸内の各コドンの頻度（行列）。 -`byAA_gene`: 各遺伝子内の各アミノ酸内の各コドンの頻度（列）。 

代替の遺伝子コードを使用する場合は、カスタム `CodonDict` を提供できます。

# 例

```jldoctest
julia> codon_counts = count_codons(EXAMPLE_DATA_PATH);

julia> count_matrix = codon_counts[1];

julia> codon_frequency(count_matrix, "net_genomic")[1:5]
5-element Vector{Float64}:
 0.04941242971710299
 0.017114892645228374
 0.021009352696846777
 0.022269444158755328
 0.022257296747490142

julia> codon_frequency(count_matrix, "net_genomic") |> size
(64, 1)

julia> codon_frequency(count_matrix, "net_gene") |> size
(64, 4237)
```
