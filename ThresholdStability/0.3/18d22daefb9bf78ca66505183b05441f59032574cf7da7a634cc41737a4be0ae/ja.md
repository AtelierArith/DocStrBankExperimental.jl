```
CKSVAR_to_companionFD(F, Fstar, βtilde, nlags; diff=true)
```

CKSVARモデルを、最初の差分で入る検閲変数を用いて推定したものをコンパニオン形式に変換します。デフォルト設定の`diff=true`は、検閲変数が最初の差分で入るコンパニオン形式を返します。検閲変数がレベルで入るコンパニオン形式を取得するには、`diff=false`に設定します。
