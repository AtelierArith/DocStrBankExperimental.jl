```
resolution_offset(sz = (100, 100, 1); numbers_or_alphabets="alphabets")

アルファベットまたは数字を異なるフォントサイズと背景レベルで持つ3D配列を作成します。
```

# 引数

  * `sz::Tuple`: ボリュームのサイズを表す3つの整数のタプル。デフォルトは(100, 100, 1)。最初の2つの要素は配列サイズを定義するために10倍されます。3番目の要素には異なるアルファベットまたは数字が含まれます。
  * `numbers_or_alphabets::String`: アルファベットまたは数字を使用するかどうかを表す文字列。デフォルトは"alphabets"。

# 戻り値

```
異なるフォントサイズと背景レベルを持つアルファベットまたは数字の3D配列。
```

# 例

```jldoctest
julia> resolution_test(; sz_each_section=(100, 100), num_slices=1, numbers_or_alphabets="alphabets")
```
