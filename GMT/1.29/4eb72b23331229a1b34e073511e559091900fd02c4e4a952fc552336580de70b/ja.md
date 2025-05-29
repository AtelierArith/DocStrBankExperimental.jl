```
magref(cmd0::String="", arg1=nothing; kwargs...)
```

IGRFまたはCM4磁場モデルを評価します。

完全なドキュメントを見るには、次のように入力してください: $@? magref$

### 例

```julia
	G = magref(R=:d, onetime=2020);
	viz(G, coast=true)
```
