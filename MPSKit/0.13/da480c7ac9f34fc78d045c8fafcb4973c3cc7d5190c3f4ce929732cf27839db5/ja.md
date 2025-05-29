```
excitations(H, algorithm::QuasiparticleAnsatz, ψ::FiniteQP, [left_environments],
            [right_environments]; num=1) -> (energies, states)
excitations(H, algorithm::QuasiparticleAnsatz, ψ::InfiniteQP, [left_environments],
            [right_environments]; num=1, solver=Defaults.solver) -> (energies, states)
excitations(H, algorithm::FiniteExcited, ψs::NTuple{<:Any, <:FiniteMPS};
            num=1, init=copy(first(ψs))) -> (energies, states)
excitations(H, algorithm::ChepigaAnsatz, ψ::FiniteMPS, [envs];
            num=1, pos=length(ψ)÷2) -> (energies, states)
excitations(H, algorithm::ChepigaAnsatz2, ψ::FiniteMPS, [envs];
            num=1, pos=length(ψ)÷2) -> (energies, states)

基底状態の上にある第一励起状態とそのエネルギーギャップを計算します。

# 引数

  * `H::AbstractMPO`: 励起を見つけるための演算子
  * `algorithm`: 最適化アルゴリズム
  * `ψ::QP`: 初期準粒子の推測
  * `ψs::NTuple{N, <:FiniteMPS}`: `N` 個の第一励起状態
  * `[left_environments]`: 左の基底状態環境
  * `[right_environments]`: 右の基底状態環境

# キーワード

  * `num::Int`: 計算する励起状態の数
  * `solver`: 準粒子環境の線形ソルバーのアルゴリズム
  * `init`: 初期励起状態の推測
  * `pos`: 摂動の位置
```
