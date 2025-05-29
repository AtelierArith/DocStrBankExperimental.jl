```
EdgeModel(; kwargs...)
```

キーワード引数に従って `EdgeModel` を構築します。

主な引数:

  * `f=nothing`: コンポーネントの動的関数。`dim` が 0 の場合は何も指定しなくて構いません。
  * `g`: コンポーネントの出力関数。便利なヘルパー: [`AntiSymmetric`](@ref), [`Symmetric`](@ref), [`Fiducial`](@ref), [`Directed`](@ref) および [`StateMask`](@ref)。
  * `sym`/`dim`: 状態の記号名。`dim` が提供されると、`sym` は自動的に設定されます。
  * `outsym`/`outdim`: 出力の記号名。`outdim` が提供されると、`outsym` は自動的に設定されます。一般的に、エッジの outsym は名前付きタプル `(; src, dst)` です。ただし、`g` 関数によっては、単一のベクトルまたは何も提供しないだけで十分な場合もあります（例: `AntiSymmetric(StateMask(1:2))`）。例については [Building `EdgeModel`s](@ref) を参照してください。
  * `psym`/`pdim=0`: パラメータの記号名。`pdim` が提供されると、`psym` は自動的に設定されます。
  * `mass_matrix=I`: コンポーネントの質量行列。ベクトル `v` であることができ、その場合は `Diagonal(v)` として解釈されます。
  * `name=dim>0 ? :EdgeM : :StaticEdgeM`: コンポーネントの名前。

オプションの引数:

  * `insym`/`indim`: 入力の記号名。`indim` が提供されると、`insym` は自動的に設定されます。エッジの場合、`insym` は名前付きタプル `(; src, dst)` です。ベクトルとして与えられた場合は、自動的にタプルが作成されます。
  * `src`/`dst`: src および dst の端にある頂点のインデックスまたは名前。グラフレスコンストラクタを有効にします。
  * `ff`: コンポーネントの `FeedForwardType`。通常は `g` から自動的に推測されます。
  * `obssym`/`obsf`: 追加の「観測可能」状態を定義します。
  * `symmetadata`/`metadata`: 事前に埋め込まれたメタデータ辞書を提供します。
  * `extin=nothing`: ネットワークインデックスを持つモデルの「外部」入力を定義します。すなわち `extin=[VIndex(7,:x), ..]`。これらの入力は別の入力ベクトル `f(x, insrc, indst, extin, p, t)` および `g(ysrc, ydst, x, insrc, indst, extin, p, t)` として提供されます。

すべての記号引数はデフォルト値を設定するために使用できます。すなわち `psym=[:K=>1, :p]`。
