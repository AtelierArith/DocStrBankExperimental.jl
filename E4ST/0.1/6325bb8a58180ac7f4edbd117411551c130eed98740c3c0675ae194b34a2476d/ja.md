```
parse_lmp_results!(config, data, res_raw)
```

電力の位置的限界価格と電力フローを追加します。

| table_name | col_name    | unit                | description        |
|:---------- |:----------- |:------------------- |:------------------ |
| :bus       | :lmp_elserv | DollarsPerMWhServed | 提供されたエネルギーの位置的限界価格 |
| :branch    | :lmp_pflow  | DollarsPerMWFlow    | 電力フローの位置的限界価格      |
