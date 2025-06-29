```
imgd = dilate(img, [region])
```

最近接隣接点に対して最大フィルタを実行します。デフォルトは2次元で8接続、3次元で27接続などです。接続に含めたい次元のリストを指定できます。例えば、`region = [1,2]`はフィルタリングから3次元を除外します。

# 例

```jldoctest; setup = :(using ImageMorphology), filter = r"Array{Float64,2}|Matrix{Float64}"
julia> img = zeros(5, 5); img[3, 3] = 1.; img
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> dilate(img)
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> dilate(img, 1)
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
```
