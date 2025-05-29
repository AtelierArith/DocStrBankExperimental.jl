```julia
updatePPE!(dfg, sourceVariable; ...)
updatePPE!(dfg, sourceVariable, ppekey; warn_if_absent)

```

Update PPE data if it exists, otherwise add it. NOTE: Copies the PPE data.
