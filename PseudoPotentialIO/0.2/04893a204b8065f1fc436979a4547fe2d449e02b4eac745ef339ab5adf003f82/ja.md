```julia
struct UpfFile <: PseudoPotentialIO.PsPFile
```

ユニバーサル擬ポテンシャルフォーマットファイルの内容。

  * `checksum::Vector{UInt8}`: SHA1 チェックサム
  * `version::String`: UPF フォーマットバージョン
  * `info::Union{Nothing, String}`: 擬ポテンシャルに関するオプションの一般情報、しばしば生成入力
  * `header::PseudoPotentialIO.UpfHeader`: 様々な擬ポテンシャルメタデータ
  * `mesh::PseudoPotentialIO.UpfMesh`: 放射メッシュ、メッシュ積分係数、およびその他のメッシュ情報
  * `nlcc::Union{Nothing, Vector{Float64}}`: 放射グリッド上の擬似化されたコア電荷（`core_correction` が false の場合は無視される）
  * `local_::Union{Nothing, Vector{Float64}}`: 放射グリッド上の擬ポテンシャルの局所部分（`is_coulomb` の場合は無視される）
  * `nonlocal::PseudoPotentialIO.UpfNonlocal`: 擬ポテンシャルの非局所部分
  * `pswfc::Union{Nothing, Vector{PseudoPotentialIO.UpfChi}}`: 擬似原子価波動関数
  * `full_wfc::Union{Nothing, PseudoPotentialIO.UpfFullWfc}`: 全電子波動関数
  * `rhoatom::Vector{Float64}`: 放射グリッド上の擬似原子価電荷密度
  * `spin_orb::Union{Nothing, PseudoPotentialIO.UpfSpinOrb}`: スピン-軌道結合データ（`has_so` が false の場合は無視される）
  * `paw::Union{Nothing, PseudoPotentialIO.UpfPaw}`: PAW データ（`is_paw` が false の場合は無視される）
  * `gipaw::Union{Nothing, PseudoPotentialIO.UpfGipaw}`: GIPAW データ
