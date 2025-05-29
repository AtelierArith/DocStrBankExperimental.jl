```
nleigs(nep::NEP, Σ::AbstractVector{Complex{T}})
```

非線形固有値問題のいくつかの固有値と固有ベクトルを、`nleigs`アルゴリズムを使用して見つけます。

# 引数

  * `nep`: 非線形固有値問題のインスタンス。
  * `Σ`: 複素平面における多角形ターゲットセットの点を含むベクトル。
  * `Ξ`: 特異点集合の離散化を含むベクトル。
  * `logger`: 表示レベル (0, 1, 2)。
  * `maxdgr`: 近似の最大次数。
  * `minit`: 線形化が収束した後の最小反復回数。
  * `maxit`: 総反復回数の最大値。
  * `tollin`: 線形化の収束に対する許容誤差。
  * `isfunm` : 行列関数を使用するかどうか。
  * `static`: NLEIGSの静的バージョンを使用するかどうか。
  * `leja`: Leja-Bagby点の使用 (0 = いいえ, 1 = 拡張フェーズのみ, 2 = 常に)。
  * `nodes`: プレフィックス補間ノード (lejaが0または1のときのみ)。
  * `blksize`: 事前割り当てのためのブロックサイズ。

他のパラメータについては[`augnewton`](@ref)を参照してください。

# 戻り値

  * `λ`: ターゲットセットΣ内の非線形固有値問題NLEPの固有値のベクトル。
  * `X`: 対応する固有ベクトルの行列。
  * `res`: 対応する残差。
  * `details`: 要求された場合の解の詳細 (NleigsSolutionDetailsを参照)。

# 例

```julia-repl
julia> nep=nep_gallery("dep0");
julia> unit_square = float([1+1im, 1-1im, -1-1im,-1+1im])
julia> (λ,v)=nleigs(nep,unit_square);
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
2.4522684986758914e-12
julia> norm(compute_Mlincomb(nep,λ[2],v[:,2]))
2.7572460495529512e-12
```

# 参考文献

  * S. Guettel, R. Van Beeumen, K. Meerbergen, and W. Michiels. NLEIGS: 非線形固有値問題のための完全有理Krylov法のクラス。SIAM J. Sci. Comput., 36(6), A2842-A2864, 2014.
  * [NLEIGS Matlab toolbox](http://twr.cs.kuleuven.be/research/software/nleps/nleigs.php)

```
