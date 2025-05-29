```
triangular_lattice(Nx::Int,
                   Ny::Int;
                   kwargs...)::Lattice
```

二次元の三角格子の次元 (Nx,Ny) に対応する Lattice (LatticeBond オブジェクトの配列) を返します。デフォルトでは格子は開境界を持ちますが、キーワード引数 `yperiodic=true` を指定することで y 方向に周期的にすることができます。
