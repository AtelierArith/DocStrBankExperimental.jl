```
lp(r::LocalProjectionResult{<:SmoothLP}, λ::Real; vce=nothing)
```

スムーズなローカルプロジェクションをスムージングパラメータ `λ` で再推定します。オプションで、キーワード `vce` を使用して代替の分散共分散推定量を指定できます。
