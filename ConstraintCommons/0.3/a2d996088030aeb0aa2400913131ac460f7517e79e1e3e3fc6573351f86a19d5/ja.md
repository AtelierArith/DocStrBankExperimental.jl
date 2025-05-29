```
extract_parameters(m::Union{Method, Function}; parameters)
```

`m`の`kargs`と`parameters`の交差部分を抽出します（デフォルトは`USUAL_CONSTRAINT_PARAMETERS`）。
