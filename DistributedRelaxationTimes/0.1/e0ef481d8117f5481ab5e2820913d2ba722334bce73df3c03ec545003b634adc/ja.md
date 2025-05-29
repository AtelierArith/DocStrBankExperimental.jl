```
find_optimal_lambda(frequencies, measurements;
        method="re_im_cv",
        width_coeff=0.1,
        rbf_kernel=SqExponentialKernel())
```

Saccoccio et al. の不一致または Re-Im-クロスバリデーション手法を使用して、ハイパーパラメータ `λ` の値を提案します。

この関数の入力とキーワード引数は、`compute_DRT` 関数のそれに似ていますが、`method` キーワード引数を除いて、ユーザーが次の選択を行えるようになっています。

  * `re_im_cv` : Re-Im-クロスバリデーション
  * `discrepancy`: インピーダンススペクトルの実部と虚部を使用して計算された重み `θ` の不一致を最小化します。
