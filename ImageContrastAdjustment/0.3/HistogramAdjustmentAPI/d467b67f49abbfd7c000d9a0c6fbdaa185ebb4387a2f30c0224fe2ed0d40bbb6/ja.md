```
adjust_histogram!([out,] img, f::AbstractHistogramAdjustmentAlgorithm, args...; kwargs...)
```

`img`のヒストグラムをアルゴリズム`f`を使用して調整します。

# 出力

`out`が指定されている場合、それはインプレースで変更されます。そうでない場合、`img`がインプレースで変更されます。

# 例

アルゴリズムを`adjust_histogram!`に単純に渡すだけです：

```julia
img_adjusted = similar(img)
adjust_histogram!(img_adjusted, img, f)
```

`img`をインプレースで変更したい場合は、手動で`img_adjusted`を割り当てる必要はありません。便利なメソッドを使用してください：

```julia
adjust_histogram!(img, f)
```

参照：[`adjust_histogram`](@ref) ```
