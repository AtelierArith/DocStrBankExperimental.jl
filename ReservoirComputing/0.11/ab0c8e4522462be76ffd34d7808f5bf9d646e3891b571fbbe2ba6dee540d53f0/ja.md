```
chaotic_init([rng], [T], dims...;
    extra_edge_probability=T(0.1), spectral_radius=one(T),
    return_sparse=false)
```

デジタルカオスシステムを使用してカオスリザーバ行列を構築します [^xie2024]。

行列のトポロジーは、有限精度で動作するデジタルカオスシステムに基づく強連結隣接行列から導出されます。要求された行列の次数が有効な次数と正確に一致しない場合、最も近い有効な次数が使用されます。

# 引数

  * `rng`: 擬似乱数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: リザーバ行列の要素の型。デフォルトは`Float32`です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `extra_edge_probability`: 隣接行列に接続性を高めるために追加のランダムエッジを追加する確率。デフォルトは0.1です。
  * `desired_spectral_radius`: リザーバ行列の目標スペクトル半径。デフォルトは1です。
  * `return_sparse`: `true`の場合、関数はリザーバ行列をスパース行列として返します。デフォルトは`false`です。

# 例

```jldoctest
julia> res_matrix = chaotic_init(8, 8)
┌ Warning: 
│ 
│     リザーバ行列の次数を調整しています:
│         8 (要求) から 4 へ
│     計算されたビット精度 = 1 に基づいています。 
│ 
└ @ ReservoirComputing ~/.julia/dev/ReservoirComputing/src/esn/esn_inits.jl:805
4×4 SparseArrays.SparseMatrixCSC{Float32, Int64} with 6 stored entries:
   ⋅        -0.600945   ⋅          ⋅ 
   ⋅          ⋅        0.132667   2.21354
   ⋅        -2.60383    ⋅        -2.90391
 -0.578156    ⋅         ⋅          ⋅
```

[^xie2024]: Xie, Minzhi, Qianxue Wang, and Simin Yu. "Time Series Prediction of ESN Based on Chebyshev Mapping and Strongly Connected Topology." Neural Processing Letters 56.1 (2024): 30.
