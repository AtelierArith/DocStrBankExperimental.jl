```
struct ConjugateGradient{F<:CGFlavor,T<:Real,L<:AbstractLineSearch} <: OptimizationAlgorithm
ConjugateGradient(;
                  flavor::CGFlavor=HagerZhang(),
                  restart::Int=typemax(Int);
                  maxiter::Int=MAXITER[], # 1_000_000
                  gradtol::Real=GRADTOL[], # 1e-8
                  verbosity::Int=VERBOSITY[], # 1
                  ls_maxiter::Int=LS_MAXITER[], # 10
                  ls_maxfg::Int=LS_MAXFG[], # 20
                  ls_verbosity::Int=LS_VERBOSITY[], # 1
                  linesearch = HagerZhangLineSearch(maxiter=ls_maxiter, maxfg=ls_maxfg, verbosity=ls_verbosity))
```

共役勾配最適化アルゴリズム。

## パラメータ

  * `flavor`: 共役勾配アルゴリズムのフレーバー（βパラメータを選択するため；以下を参照）
  * `restart::Int`: 探索方向をリセットするまでの反復回数。
  * `maxiter::Int`: 最大反復回数。
  * `gradtol::T`: 勾配のノルムに対する許容誤差。
  * `verbosity::Int`: 最適化アルゴリズムの冗長性レベル。
  * `ls_maxiter::Int`: ラインサーチの最大反復回数。
  * `ls_maxfg::Int`: ラインサーチの最大関数評価回数。
  * `ls_verbosity::Int`: ラインサーチアルゴリズムの冗長性レベル。
  * `linesearch`: 使用するラインサーチアルゴリズム；カスタム値が提供されると、`ls_maxiter`、`ls_maxfg`、および`ls_verbosity`が上書きされます。

両方の冗長性レベルは以下のスキームを使用します：

  * 0: 出力なし
  * 1: 非収束時のみ警告
  * 2: アルゴリズムの最後に収束情報
  * 3: 各反復後の進捗情報
  * 4: より詳細な情報（ラインサーチのみ）

`flavor`パラメータは以下の値を取ることができます：

  * `HagerZhang(; η::Real=4 // 10, θ::Real=1 // 1)`: βのためのHager-Zhang式
  * `HestenesStiefel(; pos = true)`: βのためのHestenes-Stiefel式
  * `FletcherReeves()`: βのためのFletcher-Reeves式
  * `PolakRibiere(; pos = true)`: βのためのPolak-Ribiere式
  * `DaiYuan()`: βのためのDai-Yuan式
