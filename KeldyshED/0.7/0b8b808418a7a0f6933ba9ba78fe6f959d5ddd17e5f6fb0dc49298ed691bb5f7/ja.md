```julia
fock_states(ed::KeldyshED.EDCore) -> Vector{Vector{UInt64}}

```

与えられた厳密対角化オブジェクト `ed` に格納された不変部分空間を spanning する基底フォック状態のリストを収集します。
