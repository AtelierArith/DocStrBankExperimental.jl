遅延ペアワイズクロンケル積、またはテンソル積演算子を`AbstractMatrix`および`AbstractSciMLOperator`のサブタイプに対して計算します。`⊗(ops...)`を呼び出すことは`Base.kron(ops...)`と同等です。完全なテンソル積演算子を形成することなく、高速な演算子評価が行われます。

```
TensorProductOperator(A, B) = A ⊗ B
TensorProductOperator(A, B, C) = A ⊗ B ⊗ C

(A ⊗ B)(v) = vec(B * reshape(v, M, N) * transpose(A))
```

ここで、`M = size(B, 2)`、`N = size(A, 2)`です。

# 例

```
using SciMLOperators, LinearAlgebra

# 基本演算子を作成
A = rand(3, 3)
B = rand(4, 4)
A_op = MatrixOperator(A)
B_op = MatrixOperator(B)

# テンソル積演算子を作成
T = A_op ⊗ B_op

# 新しいインターフェースを使用してベクトルに適用
v = rand(3*4)    # アクションベクトル
u = rand(3*4)    # 更新ベクトル
p = nothing
t = 0.0

# アウトオブプレース適用
result = T(v, u, p, t)

# インプレース操作のためには、最初に演算子をキャッシュする必要があります
T_cached = cache_operator(T, v)

# インプレース適用
w = zeros(size(T, 1))
T_cached(w, v, u, p, t)

# スケーリング付きインプレース
w_orig = copy(w)
α = 2.0
β = 0.5
T_cached(w, v, u, p, t, α, β) # w = α*(T*v) + β*w_orig
```
