```
value(ex::NonlinearExpression; result::Int = 1)
```

最も最近の解法によって返された結果インデックス `result` に関連付けられた `NonlinearExpression` `ex` の値を返します。

ほとんどの使用ケースでは `getvalue` の代わりになります。

参照: [`result_count`](@ref).
