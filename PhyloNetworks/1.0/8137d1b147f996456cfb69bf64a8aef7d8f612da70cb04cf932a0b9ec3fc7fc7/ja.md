```
calibratefrompairwisedistances!(net, distances::Matrix{Float64},
    taxon_names::Vector{<:AbstractString})
```

ネットワークを、系統データから観察されたような、分類群間の入力ペアワイズ距離にできるだけ一致させるようにキャリブレーションします。`taxon_names`は、`distances`行列で考慮される順序と同じ順序で分類群のリストを提供する必要があります。最適化基準は、観察された距離とネットワークからの距離（γによって重み付けされた木の距離の重み付き平均）との間の二乗和です。ネットワークのエッジの長さが修正されます。

警告: 多くのネットワークでは、複数のキャリブレーションがペアワイズ距離データに同様に適合する可能性があります（同定可能性の欠如）。この関数は、これらの同様に良いキャリブレーションの*1つ*を出力します。

オプションの引数（デフォルト）:

  * checkpreorder (true)
  * forceMinorLength0 (false) マイナーなハイブリッドエッジの長さを0に強制する
  * ultrametric (true) ネットワークを強制する

      * 時間的一貫性: ルートから特定のノードへのすべてのパスは同じ長さでなければならず、このノードの年齢が明確に定義されること。
      * 超距離: すべてのティップがルートから同じ距離にあり、同じ年齢を持つこと。
  * NLoptMethod (`:LD_MMA`) 最適化アルゴリズムのためのもの。他のオプションには、`:LN_COBYLA`（導関数なし）が含まれます。NLoptパッケージを参照してください。
  * 最適化が停止される条件を制御するための許容値: ftolRel (1e-12)、ftolAbs (1e-10)（基準に対して）、および xtolRel (1e-10)、xtolAbs (1e-10)（枝の長さ/発散時間に対して）。
  * verbose (false)
