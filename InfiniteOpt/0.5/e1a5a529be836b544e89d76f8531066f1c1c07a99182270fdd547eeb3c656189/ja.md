```
set_derivative_method(pref::GeneralVariableRef,
                      method::AbstractDerivativeMethod
                      )::Nothing
```

`pref`に関連付けられた数値微分評価技術を指定します。`pref`が無限パラメータでない場合、`ArgumentError`がスローされます。
