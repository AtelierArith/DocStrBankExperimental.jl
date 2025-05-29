```
copy_facts(from_kb::AbstractReteRootNode, to_kb::AbstractReteRootNode, fact_types)
```

指定された `fact_type` の事実を `from_kb` から `to_kb` にコピーします。

複数の事実タイプの場合、事実タイプのコレクションに対してブロードキャストできます。
