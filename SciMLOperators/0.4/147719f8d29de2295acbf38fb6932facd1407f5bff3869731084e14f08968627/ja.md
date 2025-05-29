# `SciMLOperators.jl`

*`SciML.ai` およびそれ以降のための統一された演算子インターフェース*

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/SciMLOperators/stable)

[![codecov](https://codecov.io/gh/SciML/SciMLOperators.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/SciMLOperators.jl) [![Build Status](https://github.com/SciML/SciMLOperators.jl/workflows/CI/badge.svg)](https://github.com/SciML/SciMLOperators.jl/actions?query=workflow%3ACI)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

`SciMLOperators` は、ベクトル（または行列の列ベクトル）に作用する線形、非線形、時間依存、パラメータ依存の演算子を管理するためのパッケージです。行列フリーの演算子、迅速なテンソル積評価、事前キャッシュされた変異評価、さらに `Zygote` 互換の非変異評価のラッパーを提供します。

遅延実装された演算子代数により、ユーザーは任意のパラメータオブジェクトを受け入れる更新関数を渡すことで演算子の状態を更新できます。さらに、私たちの演算子は、`Base` および `LinearAlgebra` のメソッドに対して定義されたオーバーロードのおかげで、`AbstractMatrix` タイプのように振る舞います。

したがって、`AbstractSciMLOperator` は、線形/非線形演算子として `LinearSolve.jl` または `NonlinearSolve.jl` に渡すことができ、`ODEFunction` として `OrdinaryDiffEq.jl` に渡すことができます。`SciML` エコシステム内での使用例は、ドキュメントに提供されています。

## インストール

`SciMLOperators.jl` は登録されたパッケージであり、次のようにインストールできます。

```
julia> import Pkg
julia> Pkg.add("SciMLOperators")
```

## 例

`M`、`D`、`F` をそれぞれ行列ベース、対角行列ベース、関数ベースの `SciMLOperators` とします。

```julia
N = 4
f(u, p, t) = u .* u
f(v, u, p, t) = v .= u .* u

M = MatrixOperator(rand(N, N))
D = DiagonalOperator(rand(N))
F = FunctionOperator(f, zeros(N), zeros(N))
```

次に、以下のコードはそのまま動作します。

```julia
L1 = 2M + 3F + LinearAlgebra.I + rand(N, N)
L2 = D * F * M'
L3 = kron(M, D, F)
L4 = M \ D
L5 = [M; D]' * [M F; F D] * [F; D]
```

各 `L#` は適切なサイズの `AbstractVector` に適用できます。

```julia
p = nothing # パラメータ構造体
t = 0.0     # 時間

u = rand(N)
v = L1(u, p, t) # == L1 * u

u_kron = rand(N^3)
v_kron = L3(u_kron, p, t) # == L3 * u_kron
```

変異演算子評価の場合は、`cache_operator` を呼び出してインプレースキャッシュを生成し、操作が非割り当てになるようにします。

```julia
α, β = rand(2)

# キャッシュを割り当てる
L2 = cache_operator(L2, u)
L4 = cache_operator(L4, u)

# 割り当てなしの評価
L2(v, u, p, t) # == mul!(v, L2, u)
L4(v, u, p, t, α, β) # == mul!(v, L4, u, α, β)
```

## ロードマップ

  * [ ] [SciML エコシステムとの完全な統合](https://github.com/SciML/SciMLOperators.jl/issues/142)
  * [ ] [ブロック行列](https://github.com/SciML/SciMLOperators.jl/issues/161)
  * [x] [テンソル積評価のベンチマークと高速化](https://github.com/SciML/SciMLOperators.jl/issues/58)
  * [ ] [高速テンソル和（`kronsum`）評価](https://github.com/SciML/SciMLOperators.jl/issues/53)
  * [ ] [演算子配列代数の完全な充実](https://github.com/SciML/SciMLOperators.jl/issues/62)
  * [ ] [定数 `(u, p, t)` スライスでの演算子融合/行列チェーン乗算](https://github.com/SciML/SciMLOperators.jl/issues/51)
