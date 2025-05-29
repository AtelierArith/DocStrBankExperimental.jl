```
deepequals(t1, t2)
```

Checks whether two trees are equal by recursively calling this on all fields, except `:parent`, in order to prevent cycles. In order to ensure that the `:parent` field is not hiding something different on both trees, ensure that each is consistent first (see: `istreeconsistent`).
