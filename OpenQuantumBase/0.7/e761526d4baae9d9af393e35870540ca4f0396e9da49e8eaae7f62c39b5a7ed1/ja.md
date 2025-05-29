```julia
evaluate(H, s)

```

時間依存ハミルトニアンを時刻 `s` で評価します。単位は `GHz` です。一般的な `AbstractHamiltonian` タイプの場合、デフォルトでは `H.(s)/2/π` になります。
