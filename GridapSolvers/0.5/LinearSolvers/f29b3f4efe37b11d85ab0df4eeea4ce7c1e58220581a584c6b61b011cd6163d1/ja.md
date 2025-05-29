```
struct FGMRESSolver <: LinearSolver 
  ...
end

FGMRESSolver(m,Pr;Pl=nothing,restart=false,m_add=1,maxiter=100,atol=1e-12,rtol=1.e-6,verbose=false,name="FGMRES")
```

右前処理子 `Pr` とオプションの左前処理子 `Pl` を持つ柔軟な GMRES ソルバー。

ソルバーはサイズ `m` の基底を割り当てることから始まります。次に：

  * `restart=true` の場合、基底サイズは固定され、`m` 回の反復ごとに再起動されます。
  * `restart=false` の場合、基底サイズは増加することが許可されます。満杯になると、ソルバーは一度に `m_add` の新しい基底ベクトルを割り当てます。
