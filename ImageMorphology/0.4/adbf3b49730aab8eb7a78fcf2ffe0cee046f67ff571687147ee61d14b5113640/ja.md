```
mreconstruct(op, marker, mask; [dims])
mreconstruct(op, marker, mask, se)
```

`marker` 画像の形態学的再構成を `op` 操作によって行います。

`op` 引数は `erode` または `dilate` のいずれかで、侵食または膨張による再構成を示します。`mask` 引数は `marker` と同じ形状を持ち、出力値の範囲を制限するために使用されます。

`dims` キーワードは、ボックス形状の構造要素 [`strel_box(marker; dims)`](@ref strel_box) を構築することによって処理する次元を指定するために使用されます。一般的な構造要素の場合、半サイズは各次元に沿って `0` または `1` であることが期待されます。

定義により、再構成は `marker = select.(op(marker; dims), mask)` を安定するまで繰り返し適用することによって行われます。膨張の場合は `op, select = dilate, min`、侵食の場合は `op, select = erode, max` です。

# 例

```jldoctest; setup=:(using ImageMorphology)
julia> marker = [0 0 0 0 0; 0 9 0 0 0; 0 0 0 0 0; 0 0 0 5 0; 0 0 0 0 0; 0 9 0 0 0]
6×5 Matrix{Int64}:
 0  0  0  0  0
 0  9  0  0  0
 0  0  0  0  0
 0  0  0  5  0
 0  0  0  0  0
 0  9  0  0  0

julia> mask = [9 0 0 0 0; 0 8 7 1 0; 0 9 0 4 0; 0 0 0 4 0; 0 0 6 5 6; 0 0 9 8 9]
6×5 Matrix{Int64}:
 9  0  0  0  0
 0  8  7  1  0
 0  9  0  4  0
 0  0  0  4  0
 0  0  6  5  6
 0  0  9  8  9

julia> mreconstruct(dilate, marker, mask) # equivalent to underbuild(marker, mask)
6×5 Matrix{Int64}:
 8  0  0  0  0
 0  8  7  1  0
 0  8  0  4  0
 0  0  0  4  0
 0  0  4  4  4
 0  0  4  4  4
```

# 参照

この関数のインプレースバージョンは [`mreconstruct!`](@ref) です。膨張による再構成のためのエイリアス [`underbuild`](@ref) と、侵食による再構成のためのエイリアス [`overbuild`](@ref) もあります。

# 参考文献

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr. 1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.

```
