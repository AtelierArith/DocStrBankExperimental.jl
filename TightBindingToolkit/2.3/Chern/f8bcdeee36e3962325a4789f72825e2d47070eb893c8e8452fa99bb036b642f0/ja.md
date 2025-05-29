```julia
FindLinks(Ham::Hamiltonian, subset::Vector{Int64}) --> Tuple{Matrix{ComplexF64}, Matrix{ComplexF64}}
```

`BZ`内の各隣接点でのリンク行列を取得する関数です。k*iとk*jを接続するボンド上で、リンク行列Uは次のように定義されます：U[m, n] = <v^m[k*i]|v^n[k*j]> ここで、states[k*j[1], k*j[2]][:, m] = v^m[k*j]、k*jでのm番目の固有状態です。
