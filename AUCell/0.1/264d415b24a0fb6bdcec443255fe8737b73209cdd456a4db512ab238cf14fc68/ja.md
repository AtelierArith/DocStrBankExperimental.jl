# 例

## デフォルト: reAUCluster モード

```jldoctest
julia> pathway_AUC_main(use_testdata = "yes")
1.632442 秒 (8.44 M アロケーション: 279.642 MiB, 7.95% gc 時間, 73.87% コンパイル時間)
[ Info: INFO: 表現プロファイルのサイズは (36602, 8) でした。
1.779532 秒 (4.95 M アロケーション: 260.557 MiB, 4.14% gc 時間, 97.91% コンパイル時間)
[ Info: INFO: フィルタリングされた表現プロファイルのサイズは (7549, 8) でした。
0.000320 秒 (27 アロケーション: 34.672 KiB)
[ Info: INFO: 分析するパスウェイは 1 つです。
0.768511 秒 (1.50 M アロケーション: 99.943 MiB, 2.46% gc 時間, 95.16% コンパイル時間)
2×5 Matrix{Any}:
"pathways_name"                     ["cluster1"]                                                                                                       …  ["t"]      ["pvalue"]
"HALLMARK_TNFA_SIGNALING_VIA_NFKB"  Any["AAACCCAAGGGTTAAT-1", "AAACCCAAGAAACCAT-1", "AAACCCAAGCAACAAT-1", "AAACCCAAGCCAGAGT-1", "AAACCCACAGCAGATG-1"]     [4.92654]  [0.00263937]
```

## aucell モード

```jldoctest
julia> pathway_AUC_main(use_testdata = "yes", mode = "aucell")
  1.557316 秒 (8.44 M アロケーション: 279.659 MiB, 3.27% gc 時間, 78.85% コンパイル時間)
[ Info: INFO: 表現プロファイルのサイズは (36602, 8) でした。
  1.771720 秒 (4.95 M アロケーション: 260.557 MiB, 3.69% gc 時間, 97.39% コンパイル時間)
[ Info: INFO: フィルタリングされた表現プロファイルのサイズは (7549, 8) でした。
  0.000329 秒 (27 アロケーション: 34.672 KiB)
[ Info: INFO: 分析するパスウェイは 1 つです。
  0.667055 秒 (1.75 M アロケーション: 87.598 MiB, 3.82% gc 時間, 99.79% コンパイル時間)
[ Info: INFO: メタ情報によると、データのグループは 8 つあり、各グループは残りのサンプルと共に分析されます。
  3.153389 秒 (6.62 M アロケーション: 421.960 MiB, 3.39% gc 時間, 80.62% コンパイル時間)
2×65 Matrix{Any}:
 "GeneSet"                            "AAACCCAAGAAACCAT-1"   "AAACCCAAGAAACCAT-1"   "AAACCCAAGAAACCAT-1"  …   "AAACCCAGTACGGGAT-1"   "AAACCCAGTACGGGAT-1"   "AAACCCAGTACGGGAT-1"
 "HALLMARK_TNFA_SIGNALING_VIA_NFKB"  0.506962               0.500821               0.515332                  0.512858               0.482078               0.440029
```
