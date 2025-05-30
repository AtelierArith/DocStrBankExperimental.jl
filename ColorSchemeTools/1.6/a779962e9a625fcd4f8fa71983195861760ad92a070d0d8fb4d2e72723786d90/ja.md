```
add_alpha(cs::ColorScheme, alpha::Vector)
```

カラーシェーム `cs` のコピーを作成し、ベクトル `alpha` にあるアルファ不透明度値を設定します。

### 例

PuOr カラーシェームのコピーを作成し、最初の要素をアルファ不透明度 1.0 に設定し、最後の要素を不透明度 0.0 に設定し、中間の要素は 1.0 と 0.0 の間の値を取ります。

```julia
add_alpha(ColorSchemes.PuOr, [1.0, 0.0])
```
