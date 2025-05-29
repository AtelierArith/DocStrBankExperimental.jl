trajectory(eval::Function, p::T, reg::Region, scf::Function=transport; minE::Float64=50.0) where {T <: Particle} trajectory(eval::Function, p::T, reg::Region, scf::Function, terminate::Function) where { T <: Particle }

`p`から`minE`まで、または粒子が`reg`を出るまでの単一粒子の軌道を実行します。

  * `eval(part::T, region::Region)` 各散乱点で評価される関数
  * `p` 粒子の初期位置、方向、エネルギーを定義します（通常は `gun(T, ...)` で作成されます）
  * `reg` 軌道の最外領域（通常は `chamber()` で作成されます）
  * `scf` 輸送ダイナミクスを実装する関数 (<:Particle, Material) -> ( λ, θ, ϕ, ΔE )
  * `minE` 停止基準
  * `terminate` `T` と `Region` を受け取り、最後のステップ以外では false を返す関数（例: `terminate = (pc,r)->pc.energy < 50.0`）
