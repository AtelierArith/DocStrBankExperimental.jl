```
RapidRoute{N} <: AbstractRoute
```

RAPID（Routing Application for Parallel computatIon of Discharge）ルーティングモデルを実装します。

# フィールド

  * `adjacency::AbstractMatrix`: 河川ネットワークの接続性を表す疎行列（上流から下流へ）。
  * `infos::NamedTuple`: 標準変数名（`inputs`、`outputs`、`states`、`params`）を含むメタデータ。状態は通常 `[:discharge]` です。パラメータは `[:rapid_k, :rapid_x]` です。

# コンストラクタ

```julia
RapidRoute(; network::AbstractGraph, name::Union{Symbol, Nothing}=nothing)
```

  * `network`: 河川ネットワークを表す `Graphs.jl` 互換の有向グラフ。
  * `name`: オプションのシンボル識別子。

# 注意事項

  * 効率的な行列演算のために定式化されたマスキンガム-カンジュ法を使用します。
  * 大規模な河川ネットワークに適しています。
  * パラメータ `k`（波の速さ）と `x`（拡散）は、シミュレーション呼び出し中に `params` 引数を介してノードごとに期待されます。
