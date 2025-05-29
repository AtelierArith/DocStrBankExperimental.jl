```
assemble!(
    b::Union{AbstractArray{T,1},AbstractArray{T,2}},    # 対象ベクトル/行列
    AP::AssemblyPattern{APT,T,AT};                      # LinearForm パターン
    factor = 1)                                         # 乗算される因子
    where {APT <: APT_LinearForm, T, AT}
```

LinearForm パターン AP をベクトルまたは行列に組み立てます（アクションがベクトル値の場合）。
