```
アップサンプリング層。2つのキーワードのうちの1つを指定する必要があります：

`scale`が数値の場合、これは入力の最後の2次元（チャネルとバッチ）を除くすべてに適用されます。また、次元を個別に制御するためにタプルで指定することもできます。あるいは、キーワード`size`はタプルを受け入れ、出力の先頭次元を直接指定します。

現在サポートされているアップサンプリング`mode`と対応するNNlibのメソッドは次のとおりです：

  * `:nearest` -> [`NNlib.upsample_nearest`](@ref)
  * `:bilinear` -> [`NNlib.upsample_bilinear`](@ref)
  * `:trilinear` -> [`NNlib.upsample_trilinear`](@ref)

# 例

```

jldoctest julia> m = Upsample(scale = (2, 3)) Upsample(:nearest, scale = (2, 3))

julia> m(ones(2, 2, 1, 1)) |> size (4, 6, 1, 1)

julia> m = Upsample(:bilinear, size = (4, 5)) Upsample(:bilinear, size = (4, 5))

julia> m(ones(2, 2, 1, 1)) |> size (4, 5, 1, 1) ```
