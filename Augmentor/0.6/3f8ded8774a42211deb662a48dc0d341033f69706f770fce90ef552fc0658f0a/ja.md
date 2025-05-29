```
augment([img], pipeline) -> out
augment(img=>mask, pipeline) -> out
```

与えられた画像 `img` に対して、指定された `pipeline` の操作を順次適用し、結果の画像 `out` を返します。2 番目のメソッドについては、以下のセマンティックラッパーを参照してください。

```julia-repl
julia> img = testpattern();

julia> out = augment(img, FlipX() |> FlipY())
3×2 Array{Gray{N0f8},2}:
[...]
```

パラメータ `img` は単一の画像であるか、複数の画像のタプルであることができます。`img` が画像のタプルである場合、その要素は概念的に接続されていると見なされます。したがって、タプル内のすべての画像は、パイプラインを通じて全く同じ経路をたどります。ランダム性が関与している場合でも同様です。これは、入力と出力の両方が正確に同じ方法で変換される必要がある画像セグメンテーションの目的に役立ちます。

```julia
img1 = testpattern()
img2 = Gray.(testpattern())
out1, out2 = augment((img1, img2), FlipX() |> FlipY())
```

パラメータ `pipeline` は `Augmentor.Pipeline`、`Augmentor.Operation` のタプル、または単一の `Augmentor.Operation` であることができます。

```julia
img = testpattern()
augment(img, FlipX() |> FlipY())
augment(img, (FlipX(), FlipY()))
augment(img, FlipX())
```

`img` が省略された場合、Augmentor は関数 [`testpattern`](@ref) によって提供された拡張テスト画像を入力画像として使用します。

```julia
augment(FlipX())
```

## セマンティックラッパー

入力をセマンティックラッパーでラップすることにより、より柔軟な拡張パイプラインを定義することが可能です。セマンティックラッパーは入力の意味を決定し、その入力に対して適切な操作のみが適用されることを保証します。

現在実装されているセマンティックラッパーは次のとおりです：

  * [`Augmentor.Mask`](@ref): セグメンテーションマスクをラップします。空間変換のみを許可します。

    これに便利な使用法は `augment(img => mask, pipeline)` です。

### 例

```jldoctest
using Augmentor
using Augmentor: unwrap, Mask

img, mask = testpattern(), testpattern()
pl = Rotate90() |> GaussianBlur(3)

aug_img, aug_mask = unwrap.(augment((img, Mask(mask)), pl))
# 同等の使用法
aug_img, aug_mask = augment(img => mask, pl)

# GaussianBlur は `mask` に対してスキップされます
aug_mask == augment(mask, Rotate90())

# 出力

true
```
