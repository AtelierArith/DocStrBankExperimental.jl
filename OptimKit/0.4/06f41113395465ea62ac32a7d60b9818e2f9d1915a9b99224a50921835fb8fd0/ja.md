```
optimize(fg, x, alg;
              precondition=_precondition,
              (finalize!)=_finalize!,
              hasconverged=DefaultHasConverged(alg.gradtol),
              shouldstop=DefaultShouldStop(alg.maxiter),
              retract=_retract, inner=_inner, (transport!)=_transport!,
              (scale!)=_scale!, (add!)=_add!,
              isometrictransport=(transport! == _transport! && inner == _inner))
-> x, f, g, numfg, history
```

目的関数 `fg` の最初の値を最小化するために最適化を行います。ここで、2番目の値には勾配が含まれ、点 `x` から始めて、`GradientDescent`、`ConjugateGradient`、または `LBFGS` のインスタンスであるアルゴリズム `algorithm` を使用します。

最終的な点 `x`、対応する関数値 `f` と勾配 `g`、`fg` への呼び出しの総数、異なる反復にわたる勾配ノルムの履歴を返します。

アルゴリズムは、`hasconverged(x, f, g, norm(g))` が `true` を返すか、`shouldstop(x, f, g, numfg, numiter, time)` が `true` を返すまで実行されます。後者のケースが前者の前に発生した場合は、収束の失敗と見なされ、警告が発行されます。

キーワード引数は次のとおりです：

  * `precondition::Function`: 現在の点 `x` と勾配 `g` を受け取り、前処理された勾配を返す関数。デフォルトでは、恒等関数が使用されます。
  * `finalize!::Function`: 最終点 `x`、関数値 `f`、勾配 `g`、および反復回数を受け取り、`x`、`f`、および `g` の可能性のある修正値を返す関数。デフォルトでは、恒等関数が使用されます。修正された値が最適化アルゴリズム内で不整合を引き起こさないことを保証するのはユーザーの責任です。
  * `hasconverged::Function`: 現在の点 `x`、関数値 `f`、勾配 `g`、および勾配のノルムを受け取り、最適化が収束したかどうかを示すブール値を返す関数。デフォルトでは、勾配のノルムがアルゴリズムインスタンスにエンコードされた許容誤差 `gradtol` と比較されます。
  * `shouldstop::Function`: 現在の点 `x`、関数値 `f`、勾配 `g`、`fg` への呼び出しの数、反復回数、およびこれまでに費やした時間を受け取り、最適化を停止すべきかどうかを示すブール値を返す関数。デフォルトでは、反復回数がアルゴリズムインスタンスにエンコードされた最大反復回数と比較されます。

アルゴリズムインスタンスの作成に関する詳細や、残りのキーワード引数の意味とそのデフォルト値については、このパッケージのREADMEを確認してください。

!!! 警告

```
`hasconverged` と `shouldstop` のデフォルト値は、このパッケージの以前のバージョンとの連続性を確保するために提供されています。ただし、この動作は将来的に変更される可能性があります。
```

また、[`GradientDescent`](@ref)、[`ConjugateGradient`](@ref)、[`LBFGS`](@ref) も参照してください。
