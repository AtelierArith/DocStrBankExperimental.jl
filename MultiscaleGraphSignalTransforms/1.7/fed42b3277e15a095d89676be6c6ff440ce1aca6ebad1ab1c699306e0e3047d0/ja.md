function dvec_Threshold(dvec::Array{Float64}, SORH::String, keep::Float64,                 GP::GraphPart, BS::BasisSpec)

HGLET / GHWT係数のしきい値処理

### 入力引数

  * `dvec::Array{Float64,2}`        拡張係数のベクトル
  * `SORH::String`        ソフト（'s'）またはハード（'h'）しきい値処理を使用
  * `keep::Float64`        0と1の間の割合で、保持すべき係数の数を示す
  * `GP::GraphPart`          スケーリング係数を特定するために使用されるGraphPartオブジェクト
  * `BS::BasisSpec`          スケーリング係数を特定するために使用されるBasisSpecオブジェクト

### 出力引数

  * `dvec_new::Vector{Float64}`        しきい値処理された拡張係数
  * `kept::Float64`        保持された係数の数
