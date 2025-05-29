```
set_supports(pref::GeneralVariableRef, supports::Union{Real, Vector{<:Real}};
             [force::Bool = false])::Nothing
```

単一の無限パラメータ `pref` に関連付けられたサポートポイントを設定します。`pref` が独立した無限パラメータでない場合、`ArgumentError` がスローされます。
