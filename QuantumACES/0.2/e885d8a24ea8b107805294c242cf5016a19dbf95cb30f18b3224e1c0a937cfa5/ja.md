```
get_marginal_wht_matrix(gate::Gate; inverse::Bool = false)
```

ゲート `gate` に対するシンプレクティック順序のウォルシュ-ハダマード変換行列を返します。これはゲートの軌道に対して周辺化されており、周辺パウリ誤差確率分布をその周辺固有値にマッピングします。また、`inverse` が `true` の場合は逆変換を返します。
