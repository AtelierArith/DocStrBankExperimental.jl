```
bootstrap!(problem::FRACProblem; nboot = 100, ndraws = 100, approximate = false)
```

この関数は、FRAC問題のパラメータをブートストラップします。これは、残差ξを再サンプリングし、市場シェアを繰り返し再シミュレーションすることによって行われます。この関数は、`problem`オブジェクトをその場で修正し、ブートストラップされたパラメータ（すべてのブートストラップを含む辞書のベクトル）を`bootstrapped_parameters_all`フィールドに追加し、デバイアスされたパラメータを`bootstrap_debiased_parameters`フィールドに追加します。後者は以下のように計算されます：

`bootstrap_debiased_parameters` = 2 β - 1/B sum(β^b)

ここで、βは元の推定値であり、β^bはb番目のブートストラップサンプルからの推定値です。
