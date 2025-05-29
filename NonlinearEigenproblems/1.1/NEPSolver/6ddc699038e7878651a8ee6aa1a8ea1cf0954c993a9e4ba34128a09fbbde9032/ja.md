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
  * `tol`: 残差の許容誤差。
  * `tollin`: 線形化の収束のための許容誤差。
  * `v`: 開始ベクトル。
  * `errmeasure`: 誤差測定のための関数 (残差ノルム)。引数 (λ,v) で呼び出されます。
  * `isfunm` : 行列関数を使用するかどうか。
  * `static`: NLEIGSの静的バージョンを使用するかどうか。
  * `leja`: Leja-Bagby点の使用 (0 = いいえ, 1 = 拡張フェーズのみ, 2 = 常に)。
  * `nodes`: プレフィックス補間ノード (lejaが0または1のときのみ)。
  * `reusefact`: 行列因子分解の再利用 (0 = いいえ, 1 = 収束した線形化の後のみ, 2 = 常に)。
  * `blksize`: 事前割り当てのブロックサイズ。
  * `return_details`: 解の詳細を返すかどうか (NleigsSolutionDetailsを参照)。
  * `check_error_every`: この反復数ごとに収束/終了をチェックします。

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
5.028313023882492e-14
julia> norm(compute_Mlincomb(nep,λ[2],v[:,2]))
1.1937025845487509e-13
```

# 参考文献

  * S. Guettel, R. Van Beeumen, K. Meerbergen, and W. Michiels. NLEIGS: 非線形固有値問題のための完全に有理なKrylov法のクラス。SIAM J. Sci. Comput., 36(6), A2842-A2864, 2014.
  * [NLEIGS Matlab toolbox](http://twr.cs.kuleuven.be/research/software/nleps/nleigs.php) (GPLライセンス)
  * [NLEIGS Matlab toolbox](https://bitbucket.org/roelvb/nleigs) (MITライセンス)

```
