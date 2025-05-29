```
get_ICD_code_range(range::String)
```

Get all codes of revision `revision` between `range[1]` and `range[2]`.

# Parameters

  * `range::String`: must be a `String` of the form `code_1-code_2`, where code*1 and code*2 are two codes (whose revision is specified by `revision`);
  * `revision::String`: must be either `"ICD-9"` or `"ICD-10"`.
