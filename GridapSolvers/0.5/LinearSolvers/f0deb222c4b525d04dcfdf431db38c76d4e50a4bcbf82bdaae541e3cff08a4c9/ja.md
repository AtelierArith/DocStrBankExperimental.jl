```
struct MINRESSolver <: LinearSolver 
  ...
end

MINRESSolver(m;Pl=nothing,maxiter=100,atol=1e-12,rtol=1.e-6,verbose=false,name="MINRES")
```

MINRESソルバー。オプションの左前処理器`Pl`を使用します。前処理器は対称かつ正定値でなければなりません。
