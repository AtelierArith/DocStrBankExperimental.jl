```
colorschemes
```

事前に定義されたカラースキームのエクスポートされた辞書：

```julia
colorschemes[:summer] |> show
   ColorScheme(
      ColorTypes.RGB{Float64}[
          RGB{Float64}(0.0,0.5,0.4), RGB{Float64}(0.01,0.505,0.4), RGB{Float64}(0.02,0.51,0.4), RGB{Float64}(0.03,0.515,0.4),
          ...
```

ランダムなカラースキームを選択するには：

```julia
scheme = rand(keys(colorschemes))
```
