```julia
updatePPE!(dfg, variablekey, ppe; warn_if_absent)

```

Update PPE data if it exists, otherwise add it – one call per `key::Symbol=:default`.

Notes

  * uses `ppe.solveKey` as solveKey.
