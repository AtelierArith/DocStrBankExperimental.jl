```
Detector(CryRadius::Real, CryLength::Real, HoleRadius::Real, HoleDepth::Real)
```

引数に応じて `well-type`、`bore-hole` または `cylindrical` ディテクタを構築して返します。引数を検査し、適切なリーフタイプコンストラクタを呼び出します。

!!! note
    最後の引数の値が `zero` の場合、欠落した引数として扱われます。


**参照:** [`CylDetector`](@ref), [`BoreDetector`](@ref), [`WellDetector`](@ref).
