```
Rotate90 <: Augmentor.AffineOperation
```

## 説明

画像を上に90度回転させます。これは特別なケースの回転であり、既存のピクセルを単に再配置することで非常に効率的に実行できます。ただし、出力画像が入力画像と同じサイズになるとは限らないため、その点に注意が必要です。

パラメータ `p` を使用して作成された場合、この操作は `Either(p=>Rotate90(), 1-p=>NoOp())` に持ち上げられます。ここで、`p` は `Rotate90` を適用する確率を示し、`1-p` は [`NoOp`](@ref) を適用する確率を示します。詳細については [`Either`](@ref) のドキュメントを参照してください。

## 使用法

```
Rotate90()

Rotate90(p)
```

## 引数

  * **`p::Number`** : オプション。操作を適用する確率。範囲は [0,1] でなければなりません。

## 参照

[`Rotate180`](@ref), [`Rotate270`](@ref), [`Rotate`](@ref), [`Either`](@ref), [`augment`](@ref)

## 例

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, Rotate90())
2×2 Matrix{Int64}:
 150   1
 200  50
```
