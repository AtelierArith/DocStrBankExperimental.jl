```
Cbase = base_color_type(C::Type)
Cbase = base_color_type(c::Colorant)
```

アルファチャンネルや指定された数値要素型なしでカラータイプを返します。`base_color_type`は[`color_type`](@ref)に似ていますが、要素型を「取り除きます」。常にパラメトリック型を返すため、数値要素型を切り替えるのに便利です。

例えば、次を比較してください。

```
base_color_type(RGB{N0f8})  === RGB
base_color_type(RGBA{N0f8}) === RGB
```

対して

```
color_type(RGB{N0f8})       === RGB{N0f8}
```

要素型の切り替えは次のように行えます。

```
c64 = base_color_type(c){Float64}(color(c))
```

`base_color_type`はアルファチャンネルを破棄します。アルファチャンネルを保持したい場合は[`base_colorant_type`](@ref)を参照してください。
