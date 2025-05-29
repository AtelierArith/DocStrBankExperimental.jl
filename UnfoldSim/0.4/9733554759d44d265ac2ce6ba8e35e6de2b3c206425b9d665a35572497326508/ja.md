```
simulate_noise(rng, t::AbstractNoise, n::Int)
```

指定されたタイプ`t`のノイズサンプルを生成します。

詳細については、各ノイズタイプのドキュメントを参照してください。実装されているノイズタイプのリストには`subtypes(AbstractNoise)`を使用してください。

# 引数

  * `rng::AbstractRNG`: プロセスを再現可能にするための乱数生成器（RNG）。
  * `t::AbstractNoise`: ノイズタイプのインスタンス、例：`PinkNoise()`。
  * `n::Int`: 生成するノイズサンプルの数。

# 戻り値

  * `Vector`: ノイズサンプルを含む長さ`n`のベクター。

# 例

```julia-repl
# ここではホワイトノイズを例として使用しますが、他のノイズタイプでも同様に機能します。
julia> noise = WhiteNoise()
WhiteNoise
  noiselevel: Int64 1
  imfilter: Int64 0

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 3)
3-element Vector{Float64}:
 -0.5325200748641231
  0.098465514284785
  0.7528865221245234
```
