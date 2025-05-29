```
struct ShiftNullspace{D,C<:RankCheck} <: MacaulayNullspaceSolver
    check::C
end
```

[`MacaulayNullspace`](@ref) から、行のシフト特性を利用して乗算行列を計算します [DBD12]。ランクチェック `check` は、ヌル空間の行インデックスの中から標準モノミアルを決定するために使用されます。

[DBD12] Dreesen, Philippe, Batselier, Kim, and De Moor, Bart. *Back to the roots: Polynomial system solving, linear algebra, systems theory.* IFAC Proceedings Volumes 45.16 (2012): 1203-1208.
