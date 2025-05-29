```
generate_forced_outages(url_in, url_out; <keyword arguments>)
```

`url_in`の内容から強制的な停止を生成し、それを`url_out`に書き込みます。少なくとも`url_in`は有効なSpineデータベースを指す必要があります。存在しない場合は、`url_out`に新しいSpineデータベースが作成されます。

ユニットの強制的な停止を生成するには、そのユニットの`mean_time_to_failure`を指定し、オプションで入力DBの期間として`mean_time_to_repair`を指定します。

パラメータ`units_unavailable`は、時間系列を保持する出力DBのユニットに対して書き込まれます。

# 引数

  * `alternative::String=""`: 空でない場合、出力DBの指定された代替に結果を書き込みます。
  * `filters::Dict{String,String}=Dict("tool" => "object_activity_control")`: フィルタを指定するための辞書です。可能なキーは"tool"と"scenario"です。値は入力DBのツールまたはシナリオ名である必要があります。

# 例

```
using SpineOpt
m = generate_forced_outages(
    raw"sqlite:///C:\path\to\your\input_db.sqlite", 
    raw"sqlite:///C:\path\to\your\output_db.sqlite"
)
```
