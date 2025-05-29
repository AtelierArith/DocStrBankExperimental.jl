```
PrecPartialSchurKrylovKit(J, x0, nev, which = :LM; krylovdim = max(2nev, 20), verbosity = 0)
```

`which`に従って選択された`nev`の固有値の脱落に基づいて前処理器を構築します。部分シュア分解が計算され（行列フリー）、`KrylovKit.jl`パッケージを使用して、そこから射影が構築されます。オプションは`EigKrylovKit()`のものと似ています。
