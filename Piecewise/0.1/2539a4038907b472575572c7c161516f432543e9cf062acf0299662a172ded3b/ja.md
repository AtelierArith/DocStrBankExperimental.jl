```
Piece(domain, [included,] rule, parameters)
```

引数 `domain::Tuple{Real, Real}` で定義された領域内の `Piece` オブジェクトのコンストラクタ。引数 `included::Tuple{Bool, Bool}` はデフォルトで `(true, true)` であり、領域の境界が領域に属するかどうかを示します。引数 `rule::Vector{Formula}` と `parameters::Vector{Vector{Any}}` は、部分の値を評価するために使用されるルールを指定します（[`Formula`](@ref)を参照）。単一の数式の場合は、`rule::Formula` と `parameters::Vector{Any}` を渡すことも可能です。

```
Piece(domain, [included,] function)
```

単一の関数での初期化。これは `Piece(domain, [included,] Formula(0, (x, a)->function(x)), Any[])` と同等です。

## フィールド

  * `domain::Tuple{Real, Real}`
  * `included::Tuple{Bool, Bool}`
  * `rule::Vector{Formula}`
  * `parameters::Vector{Vector{Any}}`

## 例

これは厳密に正の数に対する $1/x$ を表します：

```julia-repl
julia> Piece((0, Inf), (false, true), x -> 1 / x)
< Piece of type unnamed over the domain ]0.0, Inf] >

```

これは $x\in ]0, 1]$ に対する $-\log|x|$ を表します：

```julia-repl
julia> Piece((0, 1), (false, true), Formula("LOG", 1, (x, a) -> a[1] * log(abs(x))), [-1])
< Piece of type LOG over the domain ]0.0, 1.0] >

```
