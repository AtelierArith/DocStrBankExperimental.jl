```
GolubYe(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[],
        orth=KrylovDefaults.orth,
        eager=false,
        verbosity=KrylovDefaults.verbosity[])
```

は、正定値 `B` を持つエルミート（対称）一般化固有値問題 `A x = λ B x` を解くためのゴルブ・イェアルゴリズムを表します。`B` を逆にする必要はありません。推定値 `x` から始めて、`(A - ρ(x) B)` を作用させることでサイズ `krylovdim` のクリロフ部分空間を構築します。ここで、`ρ(x) = dot(x, A*x)/dot(x, B*x)` であり、ランチョスアルゴリズムを使用します。このプロセスは、最大 `maxiter` 回繰り返されます。各反復 `k>1` では、部分空間は $x_k - x_{k-1}$ を追加することでサイズ `krylovdim+1` にも拡張されます。これはLOPCG補正として知られ、マネーとイェによって提案されました。`krylovdim=2` の場合、このアルゴリズムは `LOPCG` と同等になります。
