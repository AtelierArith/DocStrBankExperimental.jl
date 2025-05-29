```
SpArray{T}(undef, dims...)
```

`SpArray`はブロック単位のスパース配列です。`SpArray`では、組み込みの`Array`のように自由に値を変更することはできません。例えば、`setindex!`を試みても、エラーなしに何も変更されません。

```jldoctest sparray
julia> A = SpArray{Float64}(undef, 5, 5)
5×5 SpArray{Float64, 2}:
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅

julia> A[1,1]
0.0

julia> A[1,1] = 2 # エラーなし
2

julia> A[1,1] # まだゼロ
0.0
```

これは、インデックス `(1,1)` が位置するブロックがまだアクティブでないためです。ブロックをアクティブにするには、`update_block_sparsity!(A, spy)` を使用してスパースパターンを更新する必要があります。ここで、`spy` は `Tesserae.blocksize(A)` を持っている必要があります。

```jldoctest sparray
julia> spy = trues(Tesserae.blocksize(A))
1×1 BitMatrix:
 1

julia> update_block_sparsity!(A, spy) # 戻り値は `A` に割り当てられた要素の数を示します。
64

julia> A .= 0;

julia> A[1,1] = 2
2

julia> A
5×5 SpArray{Float64, 2}:
 2.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
```
