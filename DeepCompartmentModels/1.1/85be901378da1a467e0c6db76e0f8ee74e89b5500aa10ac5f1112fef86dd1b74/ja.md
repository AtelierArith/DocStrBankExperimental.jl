```
AddGlobalParameters(out_dim, loc; init_theta, activation)
```

入力ベクトルに学習可能なグローバルパラメータ `θ` をインデックス `loc` に追加して、サイズ `out_dim` のベクトルを作成します。

# 引数:

  * `out_dim::Int`: 結果の出力ベクトルの長さ。
  * `loc::Int`: 出力ベクトルにおける θ のインデックス。
  * `init_theta`: `θ` の初期化関数。WeightInitializers.jl から。デフォルト = glorot_uniform。
  * `activation`: `θ` に使用する活性化関数。デフォルト = softplus。

# 例

```jldoctest
julia> layer = AddGlobalParameters(4, [2, 4])
AddGlobalParameters()  # 2 パラメータ、プラス 16 非学習可能
 
julia> layer([1; 2;;], ps, st)[1] # y と st を返す
4×1 Matrix{Float32}:
 1.0
 θ₁
 2.0
 θ₂
```
