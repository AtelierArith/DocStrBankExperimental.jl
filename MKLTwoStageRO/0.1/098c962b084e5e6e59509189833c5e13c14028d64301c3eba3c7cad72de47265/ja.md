```
solve(model::TSROModel; algorithm::TSRO_Algorithm) -> y_star, objv, recourse
```

二段階ロバスト最適化モデル `model` をアルゴリズム `algorithm` で解きます。

# 引数

  * `model::TSROModel`: 解くべき二段階ロバスト最適化モデル。

# キーワード

  * `algorithm::TSRO_Algorithm`: 解法アルゴリズム。

# 戻り値

  * `y_star`: 第一段階の最適決定。
  * `objv`: 二段階ロバスト最適化問題の最適目的値。
  * `recourse`: 不確実性が明らかになったときの第二段階の最適決定と再資源問題の最適目的値を得るための再資源関数、すなわち recourse(û) -> x_star, RPobjv。

# 例

### ケース-1:

```julia
using MKLTwoStageRO

c = [2]; b = [1];
A = [0;;]; d = [0]; 
G = [1;;]; h = [0]; E = [-1;;]; M = [-1;;];
Sy = [ZeroOne()]; Sx = [Rplus()]; 
UncSet = polyhedron(HalfSpace([1], 1) ∩ HalfSpace([-1], 0)) # 0 <= u <= 1
model = TSROModel(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
bdcp = BDCP()
y_star, objv, recourse = solve(model; algorithm=bdcp)
û = [0.5]
x_star, RPobjv = recourse(û)
```

### ケース-2:

```julia
using MKLTwoStageRO

c = [1, 2]; b = [3];
A = [4 5]; d = [6]; 
G = [1;;]; h = [2]; E = [-3 -4]; M = [-5 -6];
Sx = [Rplus()]; Sy = [Rplus(), ZeroOne()];
UncMod = Model()
u0 = [0, 0]
@variable(UncMod, u[1:2])
@variable(UncMod, -1 <= δ[1:2] <= 1)
@constraint(UncMod, u == u0 + δ)
model = TSROModel(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
ccg = CCG()
y_star, objv, recourse = solve(model; algorithm=ccg)
û = [0.5, -0.5]
x_star, RPobjv = recourse(û)
```

### ケース-3:

```julia
using MKLTwoStageRO

c = [1, 2]; b = [3];
A = [4 5]; d = [6]; 
G = [1;;]; h = [2]; E = [-3 -4]; M = [-5 -6];
Sx = [Rplus()]; Sy = [Rplus(), ZeroOne()];
UncMod = Model()
u0 = [0, 0]
@variable(UncMod, u[1:2])
@variable(UncMod, -1 <= δ[1:2] <= 1)
@constraint(UncMod, u == u0 + δ)
model = TSROModel(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
eccg = ECCG()
y_star, objv, recourse = solve(model; algorithm=eccg)
û = [0.5, -0.5]
x_star, RPobjv = recourse(û)
```

### ケース-4:

```julia
using MKLTwoStageRO
# ユーザーが並列化を希望する場合は、次のコードに置き換えます：
# using Distributed # ユーザーが並列化を希望する場合
# addprocs(5)
# @everywhere using MKLTwoStageRO
using GLMakie # ユーザーが可視化を希望する場合

# 不確実データ生成
u1 = 0.5 .+ 4 * rand(300)
u2 = 2 ./ u1 + 0.3 * randn(300) .+ 1
X = [u1'; u2']

# MKLベースの不確実性セット構築
algor = HessianMKL(verbose=false)
U = mklocsvmtrain(X, 21; kernel="DPDK", algorithm=algor, q_mode="randomly", ν=0.01, μ=0.05)
# U = mklocsvmtrain(X, 50; kernel="DPDK", algorithm=algor, q_mode="randomly", ν=0.01, μ=0.05, num_batch=5) # ユーザーが並列化を希望する場合
mklocsvmplot(U; backend=GLMakie) # MKL不確実性セットを可視化

# 二段階ROモデルのインスタンス化
a = [400, 414, 326, 18, 25, 20]
b = [22, 33, 20, 33, 23, 25]
E = [5 0 0 -1 0 0; 0 5 0 0 -1 0; 0 0 5 0 0 -1]
e = [0.0, 0.0, 0.0]
B = [-1.0 0.0 0.0 -1.0 0.0 0.0; 0.0 -1.0 0.0 0.0 -1.0 0.0; 0.0 0.0 -1.0 0.0 0.0 -1.0; 1.0 1.0 1.0 0.0 0.0 0.0; 0.0 0.0 0.0 1.0 1.0 1.0]
c = [0.0, 0.0, 0.0, 0.0, 0.0]
A = [0.0 0.0 0.0 1.0 0.0 0.0; 0.0 0.0 0.0 0.0 1.0 0.0; 0.0 0.0 0.0 0.0 0.0 1.0; 0.0 0.0 0.0 0.0 0.0 0.0; 0.0 0.0 0.0 0.0 0.0 0.0]
C = [0.0 0.0; 0.0 0.0; 0.0 0.0; -1.0 0.0; 0.0 -1.0]
Sx = [ZeroOne(3), Rplus(3)]
Sy = [Rplus(6)]
model = TSROModel(a, b, E, e, B, c, A, C, Sx, Sy, U)

# MKLCCGアルゴリズムを使用してモデルを解く
mklccg = MKLCCG()
x_star, objv, recourse = solve(model; algorithm=mklccg)

# 不確実性が明らかになった後の再資源決定を取得
û = [2.0, 3.0] # これは不確実性の観測であると仮定
y_star, RPobjv = recourse(û)
```
