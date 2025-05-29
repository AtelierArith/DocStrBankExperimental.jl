```
VertexModel(; kwargs...)
```

キーワード引数に従って `VertexModel` を構築します。

主な引数:

  * `f=nothing`: コンポーネントの動的関数。`dim` が 0 の場合は何も指定しなくて構いません。
  * `g`: コンポーネントの出力関数。便利なヘルパー: [`StateMask`](@ref)
  * `sym`/`dim`: 状態の象徴的な名前。`dim` が提供されると、`sym` は自動的に設定されます。
  * `outsym`/`outdim`: 出力の象徴的な名前。`outdim` が提供されると、`outsym` は自動的に設定されます。`g` が `StateMask` の場合は自動的に推測されます。
  * `psym`/`pdim=0`: パラメータの象徴的な名前。`pdim` が提供されると、`psym` は自動的に設定されます。
  * `mass_matrix=I`: コンポーネントの質量行列。ベクトル `v` である場合、`Diagonal(v)` として解釈されます。
  * `name=dim>0 ? :VertexM : :StaticVertexM`: コンポーネントの名前。

オプションの引数:

  * `insym`/`indim`: 入力の象徴的な名前。`indim` が提供されると、`insym` は自動的に設定されます。
  * `vidx`: グラフ内の頂点のインデックス、グラフレスコンストラクタを有効にします。
  * `ff`: コンポーネントの `FeedForwardType`。通常は `g` から自動的に推測されます。
  * `obssym`/`obsf`: 追加の「観測可能」状態を定義します。
  * `symmetadata`/`metadata`: 事前に埋め込まれたメタデータ辞書を提供します。
  * `extin=nothing`: ネットワークインデックスを持つモデルの「外部」入力を定義します。すなわち、`extin=[VIndex(7,:x), ..]`。これらの入力は、別の入力ベクトル `f(x, in, extin, p, t)` および `g(y, x, in, extin, p, t)` として提供されます。

すべてのシンボル引数はデフォルト値を設定するために使用できます。すなわち、`psym=[:K=>1, :p]`。
