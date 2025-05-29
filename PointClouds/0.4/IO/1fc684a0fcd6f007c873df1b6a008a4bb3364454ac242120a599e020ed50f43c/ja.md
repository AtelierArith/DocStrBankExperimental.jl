```
is_overlap(p::PointRecord)
is_overlap(points, inds = :)
```

ポイントが*オーバーラップ*としてマークされているかどうかを確認します。例えば、2つの飛行経路のオーバーラップです。これは、オーバーラップポイントのさらなる分類を可能にするために、分類（クラス12）または別のフラグ（PDRFs 6–10のみ）として記録されます。

参照: [`PointRecord`](@ref), [`classification`](@ref), [`is_key_point`](@ref), [`is_synthetic`](@ref), [`is_withheld`](@ref)
