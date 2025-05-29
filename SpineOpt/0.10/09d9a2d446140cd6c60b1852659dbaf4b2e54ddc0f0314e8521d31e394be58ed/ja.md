```
run_spineopt(url_in, url_out; <keyword arguments>)
```

`url_in`の内容を使用してSpineOptを実行し、報告書を`url_out`に書き込みます。引数`url_in`は、有効なSpineデータベースを指す`String`であるか、手動で作成されたかjsonファイルから解析された`Dict`でなければなりません。`url_out`に新しいSpineデータベースが存在しない場合は作成されます。

# 引数

  * `log_level::Int=3`: ログレベルを制御する整数。
  * `upgrade::Bool=false`: `url_in`のデータ構造を最新に自動的にアップグレードするかどうか。
  * `filters::Dict{String,String}=Dict("tool" => "object_activity_control")`: フィルタを指定するための辞書。可能なキーは"tool"と"scenario"です。値は入力DB内のツールまたはシナリオ名である必要があります。
  * `templates`: SpineOptテンプレートの上に読み込むテンプレートのコレクション。各テンプレートは`SpineOpt.template()`によって返されるものと同じ構造の`Dict`でなければなりません。
  * `mip_solver=nothing`: DBに指定されたMIPソルバーがない場合に使用するMIPソルバー。
  * `lp_solver=nothing`: DBに指定されたLPソルバーがない場合に使用するLPソルバー。
  * `use_direct_model::Bool=false`: `Model`オブジェクトを構築するために`JuMP.direct_model`を使用するかどうか。
  * `use_model_names::Bool=true`: モデル内の名前を使用するかどうか。
  * `add_bridges::Bool=false`: JuMPからソルバーへのブリッジをモデルに追加するかどうか。
  * `optimize::Bool=true`: モデルを最適化するかどうか（テストを実行するのに便利）。
  * `update_names::Bool=false`: モデルがロールした後に変数と制約の名前を更新するかどうか（コストがかかる）。
  * `alternative::String=""`: 空でない場合、出力DBの指定された代替に結果を書き込む。
  * `write_as_roll::Int=0`: 0より大きく、実行にロールホライズンがある場合、その数だけウィンドウごとに結果を書き込む。
  * `log_file_path::String=nothing`: 何も指定されていない場合、すべてのコンソール出力を指定されたパスのファイルにログします。ファイルは各呼び出しで上書きされます。
  * `resume_file_path::String=nothing`: `write_as_roll`が1以上のロールホライズン最適化にのみ関連します。指定されたパスのファイルに前回の実行からの再開データが含まれている場合、そのポイントから実行を開始します。また、モデルがロールし、結果が出力データベースに書き込まれるときに、その同じファイルに再開データを保存します。

# 例

```julia
using SpineOpt
m = run_spineopt(
    raw"sqlite:///C:\path\to\your\input_db.sqlite", 
    raw"sqlite:///C:\path\to\your\output_db.sqlite";
    filters=Dict("tool" => "object_activity_control", "scenario" => "scenario_to_run"),
    alternative="alternative_to_write_results"
)
```
