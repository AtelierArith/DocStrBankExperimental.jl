```
fluxmat(rn::ReactionSystem, pmap = Dict(); sparse=false)
```

反応 $i$ の基質複合体が複素数 $j$ である場合、$K_{ij} = k$ となる $r×c$ 行列 $K$ を返します。これは主にネットワークラプラシアンのための補助関数であり、[`laplacianmat`](@ref) です。$\frac{dx}{dt} = S*K*Φ(x)$ という有用な性質を持ち、ここで $S$ は [`netstoichmat`](@ref) またはネットストイキオメトリ行列であり、$Φ(x)$ は [`massactionvector`](@ref) です。デフォルトでは記号行列を返しますが、レート定数が `Tuple`、`Vector`、または `Dict` のシンボル-値ペアとして `pmap` を介して指定されている場合は数値行列を返します。

**警告**: 他のCatalyst関数とは異なり、`fluxmat` 関数は記号的な場合に `Matrix{Num}` を返します。これはODEの行列分解の計算を容易にし、行列のスパース形式の乗算が機能することを保証するためです。
