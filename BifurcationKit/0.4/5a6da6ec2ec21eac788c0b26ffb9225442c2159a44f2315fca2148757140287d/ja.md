```
pb = DeflatedProblem(prob, M::DeflationOperator, jactype)
```

`DeflatedProblem`を作成します。

これは、$M(u) \cdot F(u) = 0$という縮退した関数（問題）を作成します。ここで、`M`はペナルティ項をエンコードする`DeflationOperator`です。`prob`は関数をエンコードする`AbstractBifurcationProblem`です。これは、上級ユーザーによって直接使用されることを意図していません。

## 引数

  * `jactype`はニュートン解法のためのヤコビ行列を選択します。`Val(:autodiff)`、`Val(:fullIterative)`、`Val(:Custom)`のいずれかを指定できます。
