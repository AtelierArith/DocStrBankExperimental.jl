```
struct GMRESSolver <: LinearSolver 
  ...
end

GMRESSolver(m;Pr=nothing,Pl=nothing,restart=false,m_add=1,maxiter=100,atol=1e-12,rtol=1.e-6,verbose=false,name="GMRES")
```

GMRESソルバー、オプションの右および左の前処理器 `Pr` と `Pl` を使用します。

ソルバーはサイズ `m` の基底を割り当てることから始まります。次に：

  * `restart=true` の場合、基底のサイズは固定され、`m` 回の反復ごとに再起動されます。
  * `restart=false` の場合、基底のサイズは増加することが許可されます。満杯になると、ソルバーは `m_add` の新しい基底ベクトルを割り当てます。
