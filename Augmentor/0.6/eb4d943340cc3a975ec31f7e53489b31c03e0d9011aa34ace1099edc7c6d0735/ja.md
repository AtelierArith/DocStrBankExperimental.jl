```
Rotate270 <: Augmentor.AffineOperation
```

## 説明

画像を270度上に回転させます。これは、画像を90度下に回転させることとも説明できます。これは特別なケースの回転であり、既存のピクセルを単に再配置することで非常に効率的に実行できます。しかし、出力画像が入力画像と同じサイズになるとは限らないため、その点に注意が必要です。

パラメータ `p` を使用して作成された場合、この操作は `Either(p=>Rotate270(), 1-p=>NoOp())` に持ち上げられます。ここで、`p` は `Rotate270` を適用する確率を示し、`1-p` は [`NoOp`](@ref) を適用する確率を示します。詳細については、[`Either`](@ref) のドキュメントを参照してください。

## 使用法

```
Rotate270()

Rotate270(p)
```

## 引数

  * **`p::Number`** : オプション。操作を適用する確率。範囲は [0,1] でなければなりません。

## 参照

[`Rotate90`](@ref), [`Rotate180`](@ref), [`Rotate`](@ref), [`Either`](@ref), [`augment`](@ref)

## 例

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, Rotate270())
2×2 Matrix{Int64}:
 50  200
  1  150
```
