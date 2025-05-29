```
detect_edges!([out,] img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

`img`のエッジをアルゴリズム`f`を使用して検出します。指定されていない場合、`f`は[`Canny`](@ref ImageEdgeDetection.Canny)であると見なされます。

# 出力

`out`が指定されている場合、それはインプレースで変更されます。そうでない場合、`img`がインプレースで変更されます。

# 例

アルゴリズムを`detect_edges!`に単純に渡すだけです：

```julia
img_edges = similar(img)
detect_edges!(img_edges, img, f)
```

`img`をインプレースで変更したい場合、`img_edges`を手動で割り当てる必要はありません。便利なメソッドを使用してください：

```julia
detect_edges!(img, f)
```

参照：[`detect_edges`](@ref) ```
