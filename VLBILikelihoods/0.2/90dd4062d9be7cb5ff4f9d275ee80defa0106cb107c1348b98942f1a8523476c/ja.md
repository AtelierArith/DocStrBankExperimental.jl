```
ComplexVisLikelihood(μ::AbstractVector{<:StaticMatrix{2,2}}, Σ::AbstractVector{<:StaticMatrix{2,2, <:Real}})
```

2×2 複素可視性の空間上のガウス分布であるコヒーレンシーマトリックスの尤度分布を作成します。

## パラメータ

  * `μ`: 通常は何らかの VLBI モデルから計算される 2x2 静的行列のベクトルとして保存された平均コヒーレンシーマトリックス
  * `Σ`: 通常はデータから直接計算される測定共分散行列です。 `Σ` は 2x2 実静的行列のベクトルでなければなりません。

!!! notes
    すべてのベクトルが StructVectors{<:StaticMatrices{2,2}} として与えられると、最高のパフォーマンスが得られます。

