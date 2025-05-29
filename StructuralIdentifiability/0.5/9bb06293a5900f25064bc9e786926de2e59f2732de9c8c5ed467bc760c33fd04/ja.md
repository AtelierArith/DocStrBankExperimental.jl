```
assess_local_identifiability(dds::DDS{P}; funcs_to_check::Array{<: Any, 1}, known_ic, prob_threshold::Float64=0.99, loglevel=Logging.Info) where P <: MPolyRingElem{Nemo.QQFieldElem}
```

`funcs_to_check`内の関数の局所同定可能性/観測可能性をチェックします。結果は少なくとも`prob_threshold`の確率で正しいです。初期条件が既知で一般的であると仮定できる量のリストを`known_ic`として提供できます。
