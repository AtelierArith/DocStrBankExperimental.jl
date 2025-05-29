```
import_data(url, data, comment)
```

Spine dbにデータをインポートします。

# 引数

  * `url::String`: 対象データベースのURL。
  * `data::Dict`: インポートするデータ、以下の形式で。
  * `comment::String`: コミットメッセージ。

データDictの形式:

```
Dict(
    :object_classes => [:oc_name, ...],
    :relationship_classes => [[:rc_name, [:oc_name1, :oc_name2, ...]], ...],
    :objects => [[:oc_name, :obj_name], ...],
    :relationships => [[:rc_name, [:obj_name1, :obj_name2, ...], ...],
    :object_parameters => [[:oc_name, :param_name, default_value], ...],
    :relationship_parameters => [[:rc_name, :param_name, default_value], ...],
    :object_parameter_values => [[:oc_name, :obj_name, :param_name, value, :alt_name], ...],
    :relationship_parameter_values => [[:rc_name, [:obj_name1, :obj_name2, ...], :param_name, value, :alt_name], ...],
    :object_groups => [[:class_name, :group_name, :member_name], ...],
    :scenarios => [(:scen_name, true), ...],  # trueはアクティブフラグ、現在は使用されていません
    :alternatives => [:alt_name, ...],
    :scenario_alternatives => [(:scen_name, :alt_name, nothing), (:scen_name, :lower_alt_name, :alt_name), ...],
    :entity_alternatives => [
        [:object_class, :entity_name, :alt_name, true], ...
        [:multi_d_class, [:entity_name1, :entity_name2], :alt_name, false]
    ]
)
```

# 例

```
d = Dict(
    :object_classes => [:dog, :cat],
    :objects => [[:dog, :brian], [:dog, :spike]]
)
import_data(url, d, "arf!")
```
