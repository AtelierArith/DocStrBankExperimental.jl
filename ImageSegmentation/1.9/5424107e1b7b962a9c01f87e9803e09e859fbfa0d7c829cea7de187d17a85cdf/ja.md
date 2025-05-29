```
mask = flood(f, src, idx, nbrhood_function=diamond_iterator((3,3,...)))
```

配列 `mask` を返します。これは `src` と同じ軸を持ち、次の条件を満たす `src` のすべての要素に対して `true` とマークされます：

  * `f(src[i]) == true` を満たし、かつ
  * そのような要素が開始点 `idx`（整数インデックスまたは `CartesianIndex`）に接続されている。

これは、`f` が開始値 `src[idx]` に対して `false` と評価される場合にエラーをスローします。接続の感覚は `nbrhood_function` によって定義され、[`ImageSegmentation.diamond_iterator`](@ref) と [`ImageSegmentation.box_iterator`](@ref) の2つの選択肢があります。

# 例

```jldoctest; setup=:(using ImageSegmentation, ImageCore)
julia> mostly_red(c) = red(c) > green(c) && red(c) > blue(c)
mostly_red (generic function with 1 method)

julia> img = repeat(LinRange(colorant"red", colorant"blue", 4), 1, 2) # red-to-blue
4×2 Matrix{RGB{Float32}}:
 RGB(1.0, 0.0, 0.0)            RGB(1.0, 0.0, 0.0)
 RGB(0.666667, 0.0, 0.333333)  RGB(0.666667, 0.0, 0.333333)
 RGB(0.333333, 0.0, 0.666667)  RGB(0.333333, 0.0, 0.666667)
 RGB(0.0, 0.0, 1.0)            RGB(0.0, 0.0, 1.0)

julia> flood(mostly_red, [img; img], 1)   # only first copy of `img` is connected
8×2 BitMatrix:
 1  1
 1  1
 0  0
 0  0
 0  0
 0  0
 0  0
 0  0
```

さらに [`flood_fill!`](@ref) を参照してください。
