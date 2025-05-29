```julia
TensorH1LagrangeBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension;
    collocatedquadrature = false,
    mapping = nothing,
)
```

ガウス-レジャンドル-ロバット点でのテンソル積基底、ガウス-レジャンドル（デフォルト）またはガウス-レジャンドル-ロバットの積分点を使用

# 引数:

  * `numbernodes1d::Int`:             1次元のガウス-レジャンドル-ロバットノードの数
  * `numberquadraturepoints1d::Int`:  1次元の積分点の数
  * `numbercomponents::Int`:          コンポーネントの数
  * `dimension::Int`:                 基底の次元

# キーワード引数:

  * `collocatedquadrature::Bool = false`:                          ガウス-レジャンドル（`false`）またはガウス-レジャンドル-ロバット（`true`）の積分点
  * `mapping::Union{Tuple{Function,Function},Nothing} = nothing`:  積分点のマッピング - ソーセージ、コスロフ-タレザー、ヘイル-トレフェセンストリップ、または変換なし

# 戻り値:

  * H1ラグランジュテンソル積基底オブジェクト

# 例:

```jldoctest
# ガウス-レジャンドル積分点を使用して共形写像から変換された基底を生成
mapping = hale_trefethen_strip_transformation(1.4);
basis = TensorH1LagrangeBasis(4, 4, 3, 2, collocatedquadrature = true, mapping = mapping);

# 検証
println(basis)

# 出力

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
```
