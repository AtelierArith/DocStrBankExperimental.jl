```
assemble!(
    A::AbstractArray{T,2},                  # 対象行列
    AP::AssemblyPattern{APT,T,AT};          # 双線形形式パターン
    apply_action_to::Int = 1,               # どの引数にアクションが適用されるか？
    factor = 1,                             # 乗算される係数
    transposed_assembly::Bool = false,      # 結果を転置するか？
    transpose_copy = Nothing)               # この行列に転置ブロックをコピーする
    where {APT <: APT_BilinearForm, T, AT}
```

Assembly of a BilinearForm BLF into given two-dimensional AbstractArray (e.g. FEMatrixBlock or a ExtendableSparseMatrix).
