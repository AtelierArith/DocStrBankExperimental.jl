```
EC_from_FCI(Norb_in, Nocc_in; target_dirs="eigenstates_fullCI", gvals_specified::Vector{Float64} = Vector{Float64}[], gvals_target=collect(-2.0:0.1:2.0), degenerate = true, delta_eps::Float64=1.0)
```

FCI波動関数からEC法によってエネルギーカーブを計算するためのメイン関数。FCI波動関数がすでに評価され、ディレクトリに保存されていると仮定します。

# 引数

  * `Norb_in::Int64`: 軌道の数。
  * `Nocc_in::Int64`: 電子の数。
  * `target_dirs::String`: FCI波動関数が保存されているディレクトリ名。
  * `gvals_specified::Vector{Float64}`: スナップショットとして使用されるgvalsのリスト。空の場合、`glob`を介して抽出されたすべてのスナップショットが使用されます。
  * 
