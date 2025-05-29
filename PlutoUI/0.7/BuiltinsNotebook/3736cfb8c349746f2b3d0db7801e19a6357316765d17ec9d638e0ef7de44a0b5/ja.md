色の入力 - ユーザーはRGB色を選択でき、色はパッケージ[Colors.jl](https://github.com/JuliaGraphics/Colors.jl)の型`Colorant`として返されます。

`default`を使用して初期値を設定します。

# 例

```julia
@bind color1 ColorPicker()
```

```julia
using Colors

@bind color2 ColorPicker(default=colorant"#aabbcc")
```
