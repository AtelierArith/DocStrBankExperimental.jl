```
solve(problem::Karger, gradient, odesolver = MagnusGL6(); timestep)
```

事前に計算された有効拡散テンソル `difftensors` を使用して、有限パルスカージャーモデル (FPK) を解きます。
