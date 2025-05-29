```julia
geometric_jacobian(state, path)

```

与えられた状態における `Mechanism` のスパニングツリー内の有向パスに関連する幾何学的ヤコビアン（基本的または空間的ヤコビアンとも呼ばれる）を計算します。（`Joint` のコレクションと移動方向）

幾何学的ヤコビアンは、`Mechanism` の関節速度ベクトル $v$ を、関節パスのターゲットのツイスト（パス内の最後の関節に続くボディ）に対して、関節パスのソース（パス内の最初の関節に先行するボディ）に対してマッピングします。

詳細は [`path`](@ref)、[`GeometricJacobian`](@ref)、[`Twist`](@ref) を参照してください。

ヤコビアンは `Mechanism` のルートフレームで計算されます。

詳細は [`geometric_jacobian!(out, state, path)`](@ref) を参照してください。
