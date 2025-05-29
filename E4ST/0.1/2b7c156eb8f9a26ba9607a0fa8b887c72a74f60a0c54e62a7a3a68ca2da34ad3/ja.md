```
mutable struct Storage <: Modification

Storage(;name, file, build_file="")
```

Storageは、特定のストレージデバイスに対して次の条件が成り立つ時間加重の連続代表時間のセットで表されます。

  * インターバル全体のネットチャージはゼロでなければならない。
  * デバイスの総チャージは最大チャージを超えてはならず、ゼロを下回ってはならない。
  * インターバルの初期チャージは0から最大チャージの間であればどこでもよく、各時間インターバルで同じ初期チャージである。

# 引数

  * `name` - [`Modification`](@ref)の名前。
  * `file` - 各行がストレージデバイスを表すストレージテーブルのファイル名。詳細は[`summarize_table(::Val{:storage})`](@ref)を参照。
  * `build_file` - 各行がビルド可能なストレージの仕様を表すビルド可能なストレージテーブルのファイル名。詳細は[`summarize_table(::Val{:build_storage})`](@ref)を参照。

# 導入された変数

  * `pcap_stor[stor_idx, yr_idx]` - ストレージデバイスの放電電力容量（MW）。
  * `pcharge_stor[stor_idx, yr_idx, hr_idx]` - 特定の時間のチャージ電力（MW）。
  * `pdischarge_stor[stor_idx, yr_idx, hr_idx]` - 特定の時間の放電電力（MW）。
  * `e0_stor[stor_idx, yr_idx, int_idx]` - 各インターバルの開始チャージエネルギー（MWh）。

# 導入された制約

  * `cons_stor_charge_bal[stor_idx, yr_idx, int_idx]` - チャージバランス方程式 - 各インターバルのネットチャージは0。
  * `cons_stor_charge_max[stor_idx, yr_idx, int_idx, _hr_idx]` - 各インターバルの各時間における蓄積エネルギーを最大値（`pcap_stor`とストレージテーブルの放電期間列の関数）未満に制約。注意：`_hr_idx`はインターバル内のインデックスであり、通常の`hr_idx`ではない。
  * `cons_stor_charge_min[stor_idx, yr_idx, int_idx, _hr_idx]` - 各インターバルの各時間における蓄積エネルギーをゼロより大きく制約。注意：`_hr_idx`はインターバル内のインデックスであり、通常の`hr_idx`ではない。
  * `cons_pcap_stor_noadd[stor_idx, yr_idx; years[yr_idx] >= storage.year_on[stor_idx]]` - 建設後に容量が非増加であることを制約。（複数年シミュレーションのみ）
  * `cons_pcap_stor_prebuild[stor_idx, yr_idx; years[yr_idx] < storage.year_on[stor_idx]]` - 建設前に容量をゼロに固定。 （複数年シミュレーションでのみ発生するべき）
  * `cons_pcap_stor_exog[stor_idx, yr_idx]` - 最初の年の未建設の外生的容量をその建設年以降の`pcap0`に等しく制約。

# 目的項目

  * `capex_obj_stor` - ストレージデバイスを建設するための資本支出、建設年にのみ非ゼロ。（`pcap_stor`、`capex`、および`year_on`の関数）
  * `fom_stor` - ストレージデバイスの固定運用および保守コスト（`pcap_stor`とストレージテーブルの`fom`の関数）
  * `vom_stor` - ストレージデバイスの変動運用および保守コスト（`pdischarge_stor`、ストレージテーブルの`vom`列、および時間重み[`get_hour_weights`](@ref)の関数）

# 電力バランス方程式

各ストレージデバイスは、`side`列によって指定された「発電」側または「負荷」側のいずれかにあることができます。

  * 「発電」側：

      * `pcharge_stor`が`pgen_bus`から引かれる
      * `pdischarge_stor`が`pgen_bus`に加算される
  * 「負荷」側：

      * `pcharge_stor`が`plserv_bus`に加算される
      * `pdischarge_stor`が`plserv_bus`から引かれる

```
