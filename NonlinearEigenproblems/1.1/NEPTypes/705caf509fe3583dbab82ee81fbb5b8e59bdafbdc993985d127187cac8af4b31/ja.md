```
struct DefaultErrmeasure <: Errmeasure
function DefaultErrmeasure(nep::NEP)
```

この `Errmeasure` を指定すると、NEP-PACK は `NEP` のタイプに基づいて適切な `Errmeasure` を決定しようとします。この動作は将来のバージョンで変更される可能性があることに注意してください。

参照: [`Errmeasure`](@ref)
