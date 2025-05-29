```
colorview(C, A)
```

は、数値配列 `A` のビューを返し、`A` の連続する要素を Colorant `C` のチャネルとして解釈します。

RGB や BGR のような型に関連するもので、`A` の要素はメモリ順序ではなく、コンストラクタ引数の順序で解釈されます（メモリ順序を使用したい場合は `reinterpretc` を参照してください）。

# 例

```jl
A = rand(3, 10, 10)
img = colorview(RGB, A)
```

関連情報: [`channelview`](@ref)
