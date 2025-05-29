```
excite!(A, [nothing], spin, rf::InstantaneousRF, [nothing])
excite!(A, B, spin, rf::RF, [workspace])
```

励起をシミュレートし、`A` と `B` を上書きします（[`excite`](@ref) のインプレースバージョン）。
