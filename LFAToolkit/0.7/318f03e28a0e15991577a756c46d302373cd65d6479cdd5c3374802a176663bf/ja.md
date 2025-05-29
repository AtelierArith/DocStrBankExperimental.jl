```julia
TensorH1LagrangeMacroBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    numberelements1;
    collocatedquadrature = false,
    mapping = nothing,
)
```

ガウス-レジャンドル-ロバット点でのテンソル積マクロ要素基底、ガウス-レジャンドル（デフォルト）またはガウス-レジャンドル-ロバットの積分点を使用

# 引数:

  * `numbernodes1d::Int`:             1次元のガウス-レジャンドル-ロバットノードの数
  * `numberquadraturepoints1d::Int`:  1次元の積分点の数
  * `numbercomponents::Int`:          コンポーネントの数
  * `dimension::Int`:                 基底の次元
  * `numberelements1d::Int`:          マクロ要素内の要素の数

# キーワード引数:

  * `collocatedquadrature::Bool = false`:                          ガウス-レジャンドル（`false`）またはガウス-レジャンドル-ロバット（`true`）の積分点
  * `mapping::Union{Tuple{Function,Function},Nothing} = nothing`:  積分点のマッピング - ソーセージ、コスロフ-タレザー、ヘイル-トレフェセンストリップ、または変換なし

# 戻り値:

  * H1ラグランジュテンソル積マクロ要素基底オブジェクト

# 例:

```jldoctest
# H1ラグランジュテンソルマクロ要素積基底を生成
basis = TensorH1LagrangeMacroBasis(4, 4, 1, 2, 2);

# ガウス-レジャンドル積分点で基底を生成
basis = TensorH1LagrangeMacroBasis(4, 4, 1, 2, 2; collocatedquadrature = true);

# 検証
println(basis)

# 出力

マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
```
