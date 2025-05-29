```julia
nanmask!(mask, A)
```

`A`が`NaN`である場所では`false`となる、次元`size(A)`のブールマスクを埋めます。
