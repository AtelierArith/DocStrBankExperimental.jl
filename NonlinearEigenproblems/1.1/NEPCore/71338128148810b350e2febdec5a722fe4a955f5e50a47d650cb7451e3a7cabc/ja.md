```
compute_MM(nep::NEP,S,V)
```

NEPに対して、$Σ_i M_i V f_i(S)$の合計を計算します。ここで、$S$と$V$は行列であり、NEPは$M(λ)=Σ_i M_i f_i(λ)$を満たします。

# 例

この例では、対角行列`S`の場合、`compute_MM`の結果が`compute_Mlincomb`を使っても計算できることを示します。

```julia-repl
julia> nep=nep_gallery("dep0");
julia> D=diagm(0 => [1,2])
2×2 Array{Int64,2}:
 1  0
 0  2
julia> V=ones(size(nep,1),2);
julia> W=compute_MM(nep,D,V);
julia> norm(W[:,1]-compute_Mlincomb(nep,D[1,1],V[:,1]))
0.0
julia> norm(W[:,2]-compute_Mlincomb(nep,D[2,2],V[:,2]))
4.440892098500626e-16
```

# 参考文献

非多項式非線形固有値問題に対する量$Σ_i M_i V f_i(S)$の性質は、以下の文献で広く使用されました：

  * D. Kressner 非線形固有値問題のためのブロックニュートン法, Numer. Math., 114 (2) (2009), pp. 355-372
  * C. Effenberger, 非線形固有値問題のための堅牢な解法, 博士論文, 2013, EPFローザンヌ

```
