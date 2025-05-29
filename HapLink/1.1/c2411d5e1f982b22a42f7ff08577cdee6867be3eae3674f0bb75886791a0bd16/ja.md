```
VariationPileup
```

`Variation`を支持するベースコールをアライメントのセット内で要約します。

# フィールド

  * `variation::Variation`: このパイルアップエントリのVariation
  * `depth::UInt`: このアライメントのセット内で`variation`の位置が出現する回数
  * `readpos::Vector{Float64}`: 各リード内の`variation`の相対位置
  * `quality::Vector{Float64}`: 各リード内の`variation`のphred品質
  * `strand::Vector{Strand}`: 各`variation`が見つかるストランド
