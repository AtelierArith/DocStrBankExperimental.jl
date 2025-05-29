```
ReserveRequirement <: Modification
```

準備要件の表現であり、地域内の適格な電力注入能力の合計（発電機と蓄電装置の両方を含む）が負荷の上にある一定の割合以上であることが制約されています。

キーワード引数：

  * `name` - 修正の名前
  * `area` - 準備要件のためにバスをグループ化するエリア。
  * `credit_gen` - 発電機のための[`Crediting`](@ref)、デフォルトは[`AvailabilityFactorCrediting`](@ref)
  * `credit_stor` - 蓄電施設のための[`Crediting`](@ref)（[`Storage`](@ref)を参照）、デフォルトは[`StandardStorageReserveCrediting`](@ref)
  * `requirements_file` - サブエリアと負荷の上にある電力容量のパーセント要件を含むテーブル。  [`summarize_table(::Val{:reserve_requirements})`](@ref)を参照
  * `flow_limits_file` - （オプション）各サブエリアから他のサブエリアへの正および負のフロー制限を含むテーブル。  [`summarize_table(::Val{:reserve_flow_limits})`](@ref)を参照。 提供されていない場合、地域間でのフローは許可されていないと見なされます。
  * `load_type` - 要件の基準となる負荷のタイプを示す`String`。 次のいずれか：

      * `plnom` - （デフォルト）、名目負荷電力。
      * `plserv` - サービスされた負荷電力。

モデル修正：

  * 変数

      * `pres_flow_<name>` - （nflow x nyr x nhr）フロー制限テーブルの各行のための準備電力フロー、前方および逆の最大フローによって制約されます。（`flow_limits_file`ファイルが提供されている場合のみ存在）
  * 式

      * `pres_total_subarea_<name>` - （nsubarea x nyr x nhr）各サブエリアのすべてのソースからの準備電力
      * `pres_gen_subarea_<name>` - （nsubarea x nyr x nhr）各サブエリアの発電機からの準備電力（容量の関数）
      * `pres_stor_subarea_<name>` - （nsubarea x nyr x nhr）蓄電ユニットからの準備電力（モデルに[`Storage`](@ref)がある場合のみ存在）
      * `pres_req_subarea_<name>` - （nsubarea x nyr x nhr）必要な準備電力（負荷の関数）、`requirements_file`および`load_type`に依存
      * `pres_flow_subarea_<name>` - （nsubarea x nyr x nhr）各サブエリアから流出する準備フロー、`pres_flow_<name>`変数の関数。（`flow_limits_file`ファイルが提供されている場合のみ存在）
  * 制約

      * `cons_pres_<name>` - （nsubarea x nyr x nhr）`pres_total_subarea_<name> ≥ pres_req_subarea_<name>`を制約します。

結果を追加：

  * `(:gen, :<name>_rebate)` - 準備要件を満たすための発電機のための総リベート。 一般的に≥ 0。 これは`(:gen, :net_total_revenue_prelim)`に追加され、電力`user`の福祉から差し引かれます。
  * `(:storage, :<name>_rebate)` - （[`Storage`](@ref)が含まれている場合のみ追加）準備要件を満たすための蓄電ユニットのための総リベート。 一般的に≥ 0。 これは`(:storage, :net_total_revenue_prelim)`に追加され、電力`user`の福祉から差し引かれます。
