```
S,V = broyden([eltype,]nep::NEP[,approxnep];kwargs)
```

非線形固有値問題を定義する nep に対して、（脱落を伴う）ブロイデン法を実行します。初期化に使用される近似 nep を提供することができ、開始行列/ベクトルの初期化に使用されます。オプションの引数 `approxnep` は、アルゴリズムを開始する方法を決定します。これは `NEP`、単位行列で開始することに対応するシンボル `:eye`、およびサイズ $n \times n$ の `Matrix` である可能性があります。 [`augnewton`](@ref) で説明されているほとんどの標準的な kwargs に加えて、脱落に使用される部分空間、基本的には固有値の数である `pmax`、および帳簿管理に `NaNs` を追加するかどうかを決定する `add_nans::Bool` をサポートしています。 `eigmethod` は `:eig`、`:eigs` または `:invpow` である可能性があります。 `:invpow` はパワー法の実装であり、遅いですが、例えば `BigFloat` に対してはうまく機能します。 kwarg `recompute_U` は、すべての脱落で `U` 行列を再計算する必要があるかどうかを決定します（これはより堅牢である可能性があります）。実装には、外部反復（脱落）に対応する `logger` と、ブロイデン法の反復に対応する `inner_logger` の2つのロガーがあります。 kwarg `check_error_every` と `print_error_every` は、エラーをチェックする頻度と印刷する頻度を決定します。複素共役対称性を持つ実問題の場合、複素共役ベクトルを自動的に追加することで計算を削減するために、kwarg `addconj=true` を設定することをお勧めします。

このメソッドは不変対を計算するため、複数の固有値を見つけることができます。返される値 (S,V) は不変対であり、固有値は S の対角にあります。固有対は [`get_deflated_eigpairs`](@ref) を使用して直接抽出できます。

# 例

```julia-repl
julia> nep=nep_gallery("dep0");
julia> S,V=broyden(nep);
julia> λ=S[1,1]
-0.15955391823299253 - 3.874865266487398e-19im
julia> minimum(svdvals(compute_Mder(nep,λ)))
1.6293996560844023e-16
julia> λ=S[2,2]
-0.5032087003825461 + 1.1969823800738464im
julia> minimum(svdvals(compute_Mder(nep,λ)))
1.1073470346550144e-15
julia> λ=S[3,3]
1.2699713558173726 + 5.342786996459857e-16im
julia> minimum(svdvals(compute_Mder(nep,λ)))
5.905315846211231e-16
julia> broyden(nep,logger=2,check_error_every=1);  # より多くの収束情報を印刷します
```

固有対を抽出するには、次のようにします。

```julia-repl
julia> (D,X)=get_deflated_eigpairs(S,V,size(nep,1));
julia> for i=1:3; @show norm(compute_Mlincomb(nep,D[i],X[:,i])); end
norm(compute_Mlincomb(nep, D[i], X[:, i])) = 8.459878994614521e-13
norm(compute_Mlincomb(nep, D[i], X[:, i])) = 1.2102336671048442e-13
norm(compute_Mlincomb(nep, D[i], X[:, i])) = 2.1012363973403225e-16
```

# 参考文献

  * Jarlebring, Broyden’s method for nonlinear eigenproblems, SIAM J. Sci. Comput., 41:A989–A1012, 2019, https://arxiv.org/pdf/1802.07322
