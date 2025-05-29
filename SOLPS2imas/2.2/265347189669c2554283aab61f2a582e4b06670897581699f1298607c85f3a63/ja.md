```
load_summary_data!(
    ids::IMASdd.dd,
    b2_parameters::Tuple{String, String, String, String}=("", "", "", "");
)
```

SOLPS入力ファイル（b2.*.parametersなど）を読み取り、解釈した後、要約IDSに高レベルのショット要約データをロードします。
