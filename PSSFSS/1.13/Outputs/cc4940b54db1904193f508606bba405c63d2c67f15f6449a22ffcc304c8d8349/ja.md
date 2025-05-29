```
extract_result(fname::AbstractString, ops::Tuple) --> Matrix
```

結果ファイルから抽出された出力の行列を返します。 `ops` は `@outputs` マクロによって返されるタプルです。

### 例

```
ops = @outputs FGHz S11DB(H,H) S11ANG(H,H)
data = extract_result("pssfss.res", ops)
```
