```
add_alpha(cs::ColorScheme, alpha::Vector)
```

カラーシェーム `cs` のコピーを作成し、ベクター `alpha` にあるアルファ不透明度値を設定します。

### 例

PuOr カラーシェームのコピーを作成し、最初の要素のアルファ不透明度を 1.0 に、最後の要素の不透明度を 0.0 に設定し、中間の要素には 1.0 と 0.0 の間の値を取らせます。

```julia
add_alpha(ColorSchemes.PuOr, [1.0, 0.0])
```
