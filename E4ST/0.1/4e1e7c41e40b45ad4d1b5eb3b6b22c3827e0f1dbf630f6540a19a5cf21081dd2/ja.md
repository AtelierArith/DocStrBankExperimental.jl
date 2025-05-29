```
get_cf_max(data, gen_idx, year_idx, hour_idx)
```

指定された時間での最大容量係数を返します。これは、発電特性の `af`（可用性係数）とオプションの `cf_max`（容量係数）のうち、低い方に基づいています。これが `config[:cf_threshold]` 未満の場合、ゼロに丸められます。
