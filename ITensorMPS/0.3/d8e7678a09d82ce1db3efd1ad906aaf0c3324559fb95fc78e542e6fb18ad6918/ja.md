```
apply(As::Vector{<:ITensor}, M::Union{MPS, MPO}; kwargs...)
product([...])
```

ITensor `As` を MPS または MPO `M` に適用し、それらをプライムまたは非プライムインデックスのペアからのゲートまたは行列として扱います。

# キーワード

  * `cutoff::Real`: 特異値切断のカットオフ。
  * `maxdim::Int`: 最大 MPS/MPO 次元。
  * `apply_dag::Bool = false`: ゲートとゲートのダガーを適用する（MPO の進化にのみ関連）。
  * `move_sites_back::Bool = true`: ITensor が MPS または MPO に適用された後、MPS または MPO のサイトを元の位置に戻す。

# 例

MPS に一サイトゲートを適用する：

```julia
N = 3

ITensors.op(::OpName"σx", ::SiteType"S=1/2", s::Index) =
  2*op("Sx", s)

ITensors.op(::OpName"σz", ::SiteType"S=1/2", s::Index) =
  2*op("Sz", s)

# 演算子リストを作成します。
os = [("σx", n) for n in 1:N]
append!(os, [("σz", n) for n in 1:N])

@show os

s = siteinds("S=1/2", N)
gates = ops(os, s)

# 初期状態 |↑↑↑⟩
ψ0 = MPS(s, "↑")

# ゲートを適用します。
ψ = apply(gates, ψ0; cutoff = 1e-15)

# 正確な（完全な）波動関数とテスト
prodψ = apply(gates, prod(ψ0))
@show prod(ψ) ≈ prodψ

# 結果は次のとおりです：
# σz₃ σz₂ σz₁ σx₃ σx₂ σx₁ |↑↑↑⟩ = -|↓↓↓⟩
@show inner(ψ, MPS(s, "↓")) == -1
```

非局所の二サイトゲートと一サイトゲートを MPS に適用する：

```julia
# 2サイトゲート
function ITensors.op(::OpName"CX", ::SiteType"S=1/2", s1::Index, s2::Index)
  mat = [1 0 0 0
         0 1 0 0
         0 0 0 1
         0 0 1 0]
  return itensor(mat, s2', s1', s2, s1)
end

os = [("CX", 1, 3), ("σz", 3)]

@show os

# 状態 |↓↑↑⟩ から始める
ψ0 = MPS(s, n -> n == 1 ? "↓" : "↑")

# 結果は次のとおりです：
# σz₃ CX₁₃ |↓↑↑⟩ = -|↓↑↓⟩
ψ = apply(ops(os, s), ψ0; cutoff = 1e-15)
@show inner(ψ, MPS(s, n -> n == 1 || n == 3 ? "↓" : "↑")) == -1
```

TEBD のような時間発展を行う：

```julia
# ハイゼンベルグモデルの最近接隣接項 `S⋅S` を定義する
function ITensors.op(::OpName"expS⋅S", ::SiteType"S=1/2",
                     s1::Index, s2::Index; τ::Number)
  O = 0.5 * op("S+", s1) * op("S-", s2) +
      0.5 * op("S-", s1) * op("S+", s2) +
            op("Sz", s1) * op("Sz", s2)
  return exp(τ * O)
end

τ = -0.1im
os = [("expS⋅S", (1, 2), (τ = τ,)),
      ("expS⋅S", (2, 3), (τ = τ,))]
ψ0 = MPS(s, n -> n == 1 ? "↓" : "↑")
expτH = ops(os, s)
ψτ = apply(expτH, ψ0)
```
