```julia
struct Branch{NP, IP, LN<:(AbstractVector{<:Causal.Link})}
```

`Branch`を構築し、`nodepair`の最初と二番目の要素を`links`で接続します。`indexpair`は、`nodepair`の要素が接続されるサブインデックスを決定します。

# フィールド

  * `nodepair::Any`: ブランチによって接続されたノードペア
  * `indexpair::Any`: 出力ポートと入力ポートのインデックス
  * `links::AbstractVector{<:Causal.Link}`: ブランチのリンク
