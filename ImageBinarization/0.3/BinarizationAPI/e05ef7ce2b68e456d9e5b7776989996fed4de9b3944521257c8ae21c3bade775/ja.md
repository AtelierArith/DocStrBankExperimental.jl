```
binarize!([out,] img, f::AbstractImageBinarizationAlgorithm, args...; kwargs...)
```

アルゴリズム `f` を使用して `img` を二値化します。

# 出力

`out` が指定されている場合、それはインプレースで変更されます。そうでない場合、`img` がインプレースで変更されます。

# 例

単にアルゴリズムを `binarize!` に渡すだけです：

```julia
img₀₁ = similar(img)
binarize!(img₀₁, img, f)
```

`img` をインプレースで変更したい場合は、手動で `img₀₁` を割り当てる必要はありません。便利なメソッドを使用してください：

```julia
binarize!(img, f)
```

参照： [`binarize`](@ref)
