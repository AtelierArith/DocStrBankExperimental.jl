```
shrinkageplot!(f::Indexable, m::MixedModel,
               gf::Symbol=first(fnames(m)), θref;
               ellipse=false, ellipse_scale=1, n_ellipse=5,
               cols::Union{Nothing,AbstractVector}=nothing,
               shrunk_dotcolor=(:blue, 0.25), ref_dotcolor=(:red, 0.25),
               ellipse_color=:green, ellipse_linestyle=:dash)
```

グループ化因子 `gf` のランダム効果の条件付き平均 b の散布図行列を返します。

条件付き平均は、推定されたパラメータ値でのものと `θref` でのものの2セットがプロットされます。デフォルトの `θref` は、`Λ` が単位行列の非常に大きな倍数になる結果をもたらします。対応する条件付き平均は、ペナルティなしと見なすことができます。

`cols` を指定することで、グループ化変数に関連するランダム効果のサブセットに表示を制限できます。これは、インデックスまたは項名によって指定できます。

`ellipse=true` を使用すると、相関エリプスを追加できます。エリプスの数は `n_ellipse` で制御されます。エリプスは、外側のエリプスと原点（中心）の間に均等に配置されます。エリプスのスケーリングは、乗法的な `ellipse_scale` で調整できます。エリプスが見えない場合は、`ellipse_scale` を増やしてみてください。

!!! note
    退化（特異）モデルの場合、相関エリプスも退化し、すなわち点または線に収束します。

