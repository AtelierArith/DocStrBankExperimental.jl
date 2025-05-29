```
extract_result(r::Result, ops::NTuple{N,Outfun}) --> 行列
extract_result(r::AbstractVector{Result}, ops::NTuple{N,Outfun}) --> 行列
```

`Result` インスタンスまたはベクトルから抽出された出力の行列を返します。 `ops` は `@outputs` マクロによって返される `NTuple` です。

### 例

```
results = analyze(...)
ops = @outputs FGHz s11dB(h,h) s11ang(h,h)
data = extract_result(results, ops)
# または data = extract_result(results[1], ops) # 単一行を返します
```
