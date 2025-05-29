```
PrecPartialSchurArnoldiMethod(J, N, nev, which = LM(); tol = 1e-9, kwargs...)
```

`nev` の固有値の脱落に基づいて前処理器を構築します。`which` に従って選択されます。部分シュア分解が計算され（行列フリー）、`ArnoldiMethod.jl` パッケージを使用して、そこから射影が構築されます。適切なオプションの渡し方については、`ArnoldiMethod.jl` パッケージを参照してください。
