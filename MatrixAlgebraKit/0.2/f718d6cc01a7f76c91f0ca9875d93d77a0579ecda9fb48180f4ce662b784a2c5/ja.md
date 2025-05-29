```
eigh_trunc(A; kwargs...) -> D, V
eigh_trunc(A, alg::AbstractAlgorithm) -> D, V
eigh_trunc!(A, [DV]; kwargs...) -> D, V
eigh_trunc!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

対称行列またはエルミート行列 `A` の部分的または切り捨て固有値分解を計算します。ここで、`A * V ≈ V * D` となり、等長行列 `V` には直交固有ベクトルのサブセットが含まれ、実対角行列 `D` には切り捨て戦略に従って選択された関連する固有値が含まれます。

!!! note
    バンキングメソッド `eigh_trunc!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `DV` を出力として使用できない場合があるためです。


!!! note
    [`eigh_full`](@ref) およびそのバリアントは、入力に追加の構造を仮定しているため、固有値および固有ベクトルの `eltype` を保持します。一般的な固有値分解については、[`eig_full`](@ref) を参照してください。


また、[`eigh_full(!)`](@ref eigh_full) および [`eigh_vals(!)`](@ref eigh_vals) も参照してください。
