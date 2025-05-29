```
sip_llp!
```

アルゴリズム `a::AbstractSIPAlgo` のサブプロブレム `s::AbstractSubproblemType` で使用される i 番目の SIP に対して、拡張 `t::EAGO.ExtensionType` を用いて下位レベルの問題を解決します。コマンドは `sip_llp!(t::ExtensionType, a::AbstractSIPAlgo, s::AbstractSubproblemType, ..., i, tol)` です。
