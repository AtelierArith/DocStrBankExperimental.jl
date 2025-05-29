```
GradientDescent(; 
                maxiter::Int=MAXITER[], # 1_000_000
                gradtol::Real=GRADTOL[], # 1e-8
                verbosity::Int=VERBOSITY[], # 1
                ls_maxiter::Int=LS_MAXITER[], # 10
                ls_maxfg::Int=LS_MAXFG[], # 20
                ls_verbosity::Int=LS_VERBOSITY[], # 1
                linesearch = HagerZhangLineSearch(maxiter=ls_maxiter, maxfg=ls_maxfg, verbosity=ls_verbosity))
```

勾配降下法最適化アルゴリズム。

## パラメータ

  * `maxiter::Int`: 最大反復回数。
  * `gradtol::T`: 勾配のノルムに対する許容誤差。
  * `verbosity::Int`: 最適化アルゴリズムの冗長性レベル。
  * `ls_maxiter::Int`: 線形探索の最大反復回数。
  * `ls_maxfg::Int`: 線形探索のための関数評価の最大回数。
  * `ls_verbosity::Int`: 線形探索アルゴリズムの冗長性レベル。
  * `linesearch`: 使用する線形探索アルゴリズム。カスタム値が提供されると、`ls_maxiter`、`ls_maxfg`、および`ls_verbosity`が上書きされます。

`verbosity` と `ls_verbosity` は以下のスキームを使用します：

  * 0: 出力なし
  * 1: 非収束時のみ警告
  * 2: アルゴリズムの最後に収束情報
  * 3: 各反復後の進捗情報
  * 4: より詳細な情報（線形探索のみ）
