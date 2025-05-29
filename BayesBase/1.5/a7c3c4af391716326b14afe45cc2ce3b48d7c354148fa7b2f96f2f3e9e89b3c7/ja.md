```
InvArrowheadMatrix{O, T, Z, P} <: AbstractMatrix{O}
```

`ArrowheadMatrix`の逆行列を表すラッパー構造体です。

この構造体は逆行列を明示的に計算したり保存したりすることはありません。代わりに、元の`ArrowheadMatrix`への参照を保存し、矢頭行列の特別な構造を活用した効率的な操作を実装します。

# フィールド

  * `A::ArrowheadMatrix{O, T, Z, P}`: 逆にされる元の`ArrowheadMatrix`。

# コンストラクタ

```
InvArrowheadMatrix(A::ArrowheadMatrix{O, T, Z, P})
```

与えられた`ArrowheadMatrix`をラップすることによって`InvArrowheadMatrix`を構築します。

# 操作

  * 行列-ベクトルの乗算: `A_inv * x` または `mul!(y, A_inv, x)` （A * y = x の系を解くことに相当）
  * 線形系の解法: `A_inv \ x` （元の行列による乗算に相当: A * x）
  * 密行列への変換: `convert(Matrix, A_inv)` （実際の逆行列を密行列として計算し返します）

# 例

```julia
α = 2.0
z = [1.0, 2.0, 3.0]
D = [4.0, 5.0, 6.0]
A = ArrowheadMatrix(α, z, D)
A_inv = inv(A)  # InvArrowheadMatrixを返します

# 乗算（A * y = xを解くことに相当）
x = [1.0, 2.0, 3.0, 4.0]
y = A_inv * x

# 除算（Aによる乗算に相当）
b = [5.0, 6.0, 7.0, 8.0]
x = A_inv \ b

# 密な逆行列に変換
dense_inv_A = convert(Matrix, A_inv)
```

# 注意事項

  * 逆行列は元の`ArrowheadMatrix`が非特異である場合にのみ存在します。
  * `InvArrowheadMatrix`を用いた操作は逆行列を明示的に計算するのではなく、元の行列を用いて対応する系を解きます。

# 参照

  * [`ArrowheadMatrix`](@ref): 元の矢頭行列構造。
