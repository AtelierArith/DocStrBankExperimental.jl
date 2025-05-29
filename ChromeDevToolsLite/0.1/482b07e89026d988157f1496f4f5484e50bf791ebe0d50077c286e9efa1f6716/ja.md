```
extract_cdp_result(response::Dict, path::Vector{String}=["result", "result", "value"])
```

CDPレスポンスから構成可能なパスのトラバーサルを使用して値を抽出します。パスが存在しない場合は、抽出された値または何も返しません。
