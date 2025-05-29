データ辞書から一般的に使用される事前計算データを格納する辞書を返します。主にデータ型の変換、非アクティブなコンポーネントのフィルタリング、およびグローバルに計算する必要があるシステム全体の値を格納するために使用されます。

一般的なキーには以下が含まれます：

  * `:off_angmin` と `:off_angmax`（`calc_theta_delta_bounds(data)`を参照）、
  * `:bus` – セット `{(i, bus) in ref[:bus] : bus["bus_type"] != 4}`、
  * `:gen` – セット `{(i, gen) in ref[:gen] : gen["gen_status"] == 1 && gen["gen_bus"] in keys(ref[:bus])}`、
  * `:branch` – ネットワーク内でアクティブなブランチのセット（コンポーネントのステータス値に基づく）、
  * `:arcs_from` – セット `[(i,b["f_bus"],b["t_bus"]) for (i,b) in ref[:branch]]`、
  * `:arcs_to` – セット `[(i,b["t_bus"],b["f_bus"]) for (i,b) in ref[:branch]]`、
  * `:arcs` – `arcs_from` と `arcs_to` の両方からのアークのセット、
  * `:bus_arcs` – マッピング `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs]])`、
  * `:buspairs` – （`buspair_parameters(ref[:arcs_from], ref[:branch], ref[:bus])`を参照）、
  * `:bus_gens` – マッピング `Dict(i => [gen["gen_bus"] for (i,gen) in ref[:gen]])`。
  * `:bus_loads` – マッピング `Dict(i => [load["load_bus"] for (i,load) in ref[:load]])`。
  * `:bus_shunts` – マッピング `Dict(i => [shunt["shunt_bus"] for (i,shunt) in ref[:shunt]])`。
  * `:arcs_from_dc` – セット `[(i,b["f_bus"],b["t_bus"]) for (i,b) in ref[:dcline]]`、
  * `:arcs_to_dc` – セット `[(i,b["t_bus"],b["f_bus"]) for (i,b) in ref[:dcline]]`、
  * `:arcs_dc` – `arcs_from_dc` と `arcs_to_dc` の両方からのアークのセット、
  * `:bus_arcs_dc` – マッピング `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs_dc]])`、および
  * `:buspairs_dc` – （`buspair_parameters(ref[:arcs_from_dc], ref[:dcline], ref[:bus])`を参照）、

`:ne_branch` が存在する場合、次のキーも同様の意味で利用可能です：

  * `:ne_branch`, `:ne_arcs_from`, `:ne_arcs_to`, `:ne_arcs`, `:ne_bus_arcs`, `:ne_buspairs`。
