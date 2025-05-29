```
load_summary_data!(
    ids::IMASdd.dd,
    b2_parameters::Tuple{String, String, String, String}=("", "", "", "");
)
```

Loads high level shot summary data into the summary IDS after reading and interpreting SOLPS input files, such as b2.*.parameters.
