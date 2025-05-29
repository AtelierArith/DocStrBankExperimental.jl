```
Scale(size::Integer..., σ=identity; bias=true, init=ones32)
Scale(scale::AbstractArray, [bias, σ])
```

要素ごとのレイヤーを作成します。フォワードパスは次のように与えられます：

```
y = σ.(scale .* x .+ bias)
```

これは、[`Dense`](@ref) の行列乗算 `*` の代わりに `.*` を使用します。

学習可能なスケールとバイアスは `init(size...)` と `zeros32(size...)` で初期化され、デフォルトでは `init=ones32` です。関数 `init` を指定したり、トレーニング可能なバイアスをオフにするには `bias=false` を使用するか、配列を明示的に提供することができます。

[`LayerNorm`](@ref) で `affine=true` として使用されます。

# 例

```jldoctest
julia> a = Flux.Scale(2)
Scale(2)            # 4 パラメータ

julia> Flux.trainables(a)
2-element Vector{AbstractArray}:
 Float32[1.0, 1.0]
 Float32[0.0, 0.0]

julia> a([1 2 3])
2×3 Matrix{Float32}:
 1.0  2.0  3.0
 1.0  2.0  3.0

julia> b = Flux.Scale(Float32[1 2 3 4], false, abs2)
Scale(1, 4, abs2; bias=false)  # 4 パラメータ

julia> b([1, 10])
2×4 Matrix{Float32}:
   1.0    4.0    9.0    16.0
 100.0  400.0  900.0  1600.0

julia> Flux.trainables(b)
1-element Vector{AbstractArray}:
 Float32[1.0 2.0 3.0 4.0]
```
