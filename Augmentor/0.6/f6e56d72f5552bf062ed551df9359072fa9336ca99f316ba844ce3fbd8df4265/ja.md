```
Either <: Augmentor.ImageOperation
```

## 説明

適用時に与えられた `operations` の中からランダムに選択します。これは、例えば最初に画像を90度時計回りまたは反時計回りに回転させ（両方は決して行わない）、その後に他の操作を適用したい場合に特に便利です。

パイプラインをコンパイルする際、`Either` は提供された `operations` を分析し、適用時に使用するのに適した形式を特定します。選ばれた形式は、与えられたすべての `operations` によってサポートされるように選ばれます。このようにして、`Either` を適用した結果は推論可能であり、全体のパイプラインは型安定性を保ちます（ランダム性が関与しているにもかかわらず）。

デフォルトでは、指定された各画像操作は同じ発生確率を持ちます。このデフォルトの動作は、`chance` を手動で指定することで上書きできます。

## 使用法

```
Either(operations, [chances])

Either(operations...; [chances])

Either(pairs...)

*(operations...)

*(pairs...)
```

## 引数

  * **`operations`** : 適用時にサンプリングする可能性のある選択肢を示す `Augmentor.ImageOperation` の `NTuple` または `Vararg`。
  * **`chances`** : オプション。操作がサンプリングされる相対的な確率を示します。`operations` と同じ数の要素を含む必要があります。位置引数として指定された場合は数値の `NTuple`、またはキーワード引数として指定された場合は数値の `AbstractVector` である必要があります。省略した場合、すべての操作は等しい発生確率を持ちます。
  * **`pairs`** : `Pair{<:Real,<:Augmentor.ImageOperation}` の `Vararg`。操作とその発生確率を一緒に指定するためのコンパクトな方法。

## 参照

[`NoOp`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# すべての3つの操作は等しい発生確率を持つ
augment(img, Either(FlipX(), FlipY(), NoOp()))
augment(img, FlipX() * FlipY() * NoOp())

# NoOp は FlipX または FlipY の2倍の確率で発生する
augment(img, Either(1=>FlipX(), 1=>FlipY(), 2=>NoOp()))
augment(img, Either(FlipX(), FlipY(), NoOp(), chances=[1,1,2]))
augment(img, Either((FlipX(), FlipY(), NoOp()), (1,1,2)))
augment(img, (1=>FlipX()) * (1=>FlipY()) * (2=>NoOp()))
```
