```
add_alpha(cs::ColorScheme, alpha::Real=0.5)
```

アルファ不透明度値 `alpha` を持つカラースキーム `cs` のコピーを作成します。

### 例

PuOr カラースキームのコピーを作成し、そのすべての要素のアルファ不透明度を 0.5 に設定します。

```julia
add_alpha(ColorSchemes.PuOr, 0.5)
```
