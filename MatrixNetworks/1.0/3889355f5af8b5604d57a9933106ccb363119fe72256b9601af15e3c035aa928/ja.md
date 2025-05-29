# `seeded_stochastic_heat_kernel`

確率的熱カーネルを計算します。結果は $x = \exp(-t(I - P)) s $ であり、ここで $s$ は確率的シードベクトル、$t$ は時間パラメータ、$P$ は列確率行列または部分確率行列です。

この関数は、ベクトル $x$ を返します。これは $ \| x - x*{\mbox{exact}} \|*1 \le $ `eps` を満たし、さらにこの関数は $x_{\mbox{exact}} - x \ge 0$ を保証します。

## 関数

  * 入力 A は `A::SparseMatrixCSC{V,Int}` または `A::MatrixNetwork{V}` のいずれかで、値の型 `V` に対して
  * `seeded_stochastic_heat_kernel(A,t::Float64,s)` は、以下のいずれかの形式で確率的シード `s` を提供します：
  * `seeded_stochastic_heat_kernel(A,t,s::Float64)`: s は 1/size(A,1) でなければならず、これはすべての要素が1のベクトルを使用することに対応します。
  * `seeded_stochastic_heat_kernel(A,t,s::Int)` は、単一の非ゼロ要素を持つベクトルを使用します。
  * `seeded_stochastic_heat_kernel(A,t,s::Set{Int})`
  * `seeded_stochastic_heat_kernel(A,t,s::Dict{Int,Float64})`
  * `seeded_stochastic_heat_kernel(A,t,s::SparseMatrixCSC{Float64,Int})`
  * `seeded_stochastic_heat_kernel(A,t,s::SparseVector{Float64,Int})`
  * `seeded_stochastic_heat_kernel(A,t,s::Vector{Float64})`
  * `seeded_stochastic_heat_kernel(A,t::Float64,s,eps::Float64)`: 解の許容誤差を指定します（デフォルトは `eps=eps(Float64)`）

## 入力

-`A`: 非負のエントリを持つスパース行列またはマトリックスネットワークオブジェクト   -`t`: 熱カーネルの時間の値 $0 <= t$   -`eps`: 解の許容誤差 $ 0 < eps < 1 $   -`s`: 確率的シードベクトル、これは確率的に正規化されます

## 戻り値

-`x`: 確率的熱カーネル評価の結果

## 例

```

```
