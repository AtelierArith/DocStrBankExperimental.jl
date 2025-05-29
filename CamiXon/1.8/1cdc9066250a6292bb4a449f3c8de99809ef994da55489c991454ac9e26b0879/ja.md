```
extractCore(config::String)
```

*コンパクト構成表記* で与えられた `config` から *コア構成* を抽出します。

#### 例

```
julia> extractCore("[Ar]4s¹")
"1s²2s²2p⁶3s²3p⁶"
```
