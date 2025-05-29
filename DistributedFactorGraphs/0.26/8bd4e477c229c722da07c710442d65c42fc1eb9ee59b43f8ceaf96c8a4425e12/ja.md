```julia
updatePPE!(dfg, sourceVariable; ...)
updatePPE!(dfg, sourceVariable, ppekey; warn_if_absent)

```

PPEデータが存在する場合は更新し、そうでない場合は追加します。注意：PPEデータをコピーします。
