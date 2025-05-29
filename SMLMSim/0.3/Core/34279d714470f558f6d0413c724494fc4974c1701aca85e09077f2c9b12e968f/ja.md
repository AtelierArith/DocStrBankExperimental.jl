```
GenericFluor <: Molecule
```

光物理特性を持つ蛍光体を定義します。

# フィールド

  * `γ::AbstractFloat`: 光子放出率（Hz）。デフォルト: 1e5
  * `q::Array{<:AbstractFloat}`: q[i,j]がi≠jの場合は状態iからjへの遷移率、q[i,i]は状態iからの負の退出率を示すレート行列。デフォルト: オン->オフのレートが50Hz、オフ->オンのレートが1e-2Hzの標準2状態モデル

# 例

```julia
# デフォルトパラメータを使用して蛍光体を作成する（2状態キーワードコンストラクタを使用）
fluor = GenericFluor()

# 位置引数コンストラクタを使用してカスタムパラメータで蛍光体を作成する
fluor = GenericFluor(1e5, [-50.0 50.0; 1e-2 -1e-2])

# 2状態キーワードコンストラクタを使用して蛍光体を作成する
fluor = GenericFluor(; photons=1e5, k_off=10.0, k_on=1e-1)
```
