```
WhiteNoise <: AbstractNoise
```

`randn`を使用してホワイトノイズを生成するための型 - すなわちガウスノイズです。

ノイズ値は標準正規分布𝒩(μ=0, σ=1)からサンプリングされます。つまり、約95%の値は約-2と約2の間にあります（`noiselevel = 1`の場合）。 ヒント: 手動でノイズサンプルを作成するには、[`simulate_noise`](@ref)関数を使用してください。

# フィールド

  * `noiselevel = 1`（オプション）: ノイズをスケーリングするために使用される係数。
  * `imfilter = nothing`（オプション）: `imfilter > 0`を使用して、`σ = imfilter`のガウスカーネルを使用して`Image.imfilter`でノイズを平滑化します。

# 例

```julia-repl
julia> noise = WhiteNoise()
WhiteNoise
  noiselevel: Int64 1
  imfilter: Nothing nothing

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 3)
3-element Vector{Float64}:
 -0.5325200748641231
  0.098465514284785
  0.7528865221245234
```

他にも[`PinkNoise`](@ref)、[`RedNoise`](@ref)、[`ExponentialNoise`](@ref)、[`NoNoise`](@ref)があります。
