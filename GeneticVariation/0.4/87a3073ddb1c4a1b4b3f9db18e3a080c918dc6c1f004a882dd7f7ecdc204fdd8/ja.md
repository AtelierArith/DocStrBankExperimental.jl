```
NL79(sequences)
```

ヌクレオチド多様性を計算します。これは、NeiとLiによって1979年に説明されたものです。

この指標は、サンプル集団内のすべての可能なペア間での2つのDNA配列間のサイトごとの平均ヌクレオチド差の数として定義され、しばしばギリシャ文字のπで表されます。

`Sequences`は、バイオシーケンスタイプを生成する任意の反復可能なものである必要があります。

# 例

```jldoctest
julia> testSeqs = [dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAAATTTTACCCCCGTGGG",
                   dna"AAAAATTTTACCCCCGTGGG",
                   dna"AAAACTTTTTCCCCCGTAGG",
                   dna"AAAACTTTTTCCCCCGTAGG",
                   dna"AAAAATTTTTCCCCCGGAGG",
                   dna"AAAAATTTTTCCCCCGGAGG"]
10-element Array{BioSequences.BioSequence{BioSequences.DNAAlphabet{4}},1}:
 AAAACTTTTACCCCCGGGGG
 AAAACTTTTACCCCCGGGGG
 AAAACTTTTACCCCCGGGGG
 AAAACTTTTACCCCCGGGGG
 AAAAATTTTACCCCCGTGGG
 AAAAATTTTACCCCCGTGGG
 AAAACTTTTTCCCCCGTAGG
 AAAACTTTTTCCCCCGTAGG
 AAAAATTTTTCCCCCGGAGG
 AAAAATTTTTCCCCCGGAGG

 julia> NL79(testSeqs)
 0.096

```
