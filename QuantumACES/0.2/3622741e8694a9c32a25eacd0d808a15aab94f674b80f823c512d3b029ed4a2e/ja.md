```
get_wht_matrix(n::Integer; inverse::Bool = false)
get_wht_matrix(gate::Gate; inverse::Bool = false)
```

`n`の順序のシンプレクティックに整列されたウォルシュ-アダマール変換行列を返します。これは、ゲート`gate`が作用する量子ビットの数であり、n量子ビットのパウリ誤差確率分布をその固有値にマッピングします。また、`inverse`が`true`の場合は逆変換を返します。
