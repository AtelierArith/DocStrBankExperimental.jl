```
center_longitude!(var::OutputVar, lon::Real)
```

`var`内の経度をシフトして、`lon`を中心にします。

これは、グローバル投影を0ではなく180経度にセンタリングするのに便利です。

!!! warn "非推奨"
    この関数は非推奨であり、ユーザーは代わりに[`shift_longitude`](@ref)を使用することを推奨します。

