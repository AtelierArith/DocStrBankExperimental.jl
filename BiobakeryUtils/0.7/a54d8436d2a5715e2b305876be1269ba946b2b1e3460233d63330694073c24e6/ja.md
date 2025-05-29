```
humann_profile(path::AbstractString; sample=basename(first(splitext(path))), stratified=false)
```

`HUMAnN`によって生成された単一の機能プロファイルをロードします。デフォルトでは、種に基づく内容を持つ行はスキップされます。`stratified=true`を使用すると、それらを保持します。
