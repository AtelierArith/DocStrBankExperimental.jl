```
LBFGS(m::Int = 8; 
      acceptfirst::Bool = true,
      maxiter::Int=MAXITER[], # 1_000_000
      gradtol::Real=GRADTOL[], # 1e-8
      verbosity::Int=VERBOSITY[], # 1
      ls_maxiter::Int=LS_MAXITER[], # 10
      ls_maxfg::Int=LS_MAXFG[], # 20
      ls_verbosity::Int=LS_VERBOSITY[], # 1
      linesearch = HagerZhangLineSearch(maxiter=ls_maxiter, maxfg=ls_maxfg, verbosity=ls_verbosity))
```

LBFGS最適化アルゴリズム。

## パラメータ

  * `m::Int`: 限定メモリBFGS近似のために保存する前の反復の数。
  * `maxiter::Int`: 最大反復回数。
  * `gradtol::T`: 勾配のノルムに対する許容誤差。
  * `verbosity::Int`: 最適化アルゴリズムの冗長性レベル。
  * `acceptfirst::Bool`: ラインサーチの最初のステップを受け入れるかどうか。
  * `ls_maxiter::Int`: ラインサーチの最大反復回数。
  * `ls_maxfg::Int`: ラインサーチの最大関数評価回数。
  * `ls_verbosity::Int`: ラインサーチアルゴリズムの冗長性レベル。
  * `linesearch`: 使用するラインサーチアルゴリズム。カスタム値が提供されると、`ls_maxiter`、`ls_maxfg`、および`ls_verbosity`が上書きされます。

`verbosity`と`ls_verbosity`は以下のスキームを使用します：

  * 0: 出力なし
  * 1: 非収束時のみ警告
  * 2: アルゴリズムの最後に収束情報
  * 3: 各反復後の進捗情報
  * 4: より詳細な情報（ラインサーチのみ）
