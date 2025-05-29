```
assess_local_identifiability(ode::ODE{P}; funcs_to_check::Array{<: Any, 1}, prob_threshold::Float64=0.99, type=:SE, loglevel=Logging.Info) where P <: MPolyRingElem{Nemo.QQFieldElem}
```

`funcs_to_check`内の関数の局所同定可能性/観測可能性をチェックします。結果は少なくとも`prob_threshold`の確率で正しいです。

局所同定可能性をチェックしたい特定のパラメータのコレクションがある場合は、この関数を呼び出してください。

`type`は`:SE`（単一実験同定可能性）または`:ME`（多実験同定可能性）のいずれかにすることができます。タイプが`:ME`の場合、状態は`funcs_to_check`に現れることは許可されていません。
