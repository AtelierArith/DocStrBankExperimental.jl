```
UnfoldSim.generate_events([rng::AbstractRNG, ]design::RepeatDesign{T})
```

`RepeatDesign`の場合、基になる{T}デザインに対して`generate_events`を反復的に呼び出し、結果を連結します。

`MultiSubjectDesign`の場合は、被験者でソートします。  `RepeatDesign`で`event_order_function`（例：`shuffle`）を使用する際は、対応するRNGが反復間で共有され、各反復のために深くコピーされないことに注意してください。その結果、イベントの順序は各反復で異なります。
