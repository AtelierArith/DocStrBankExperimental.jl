```
sparse_jacobian_cache(ad::AbstractADType, sd::AbstractSparsityDetection, f, x;
    fx=nothing)
sparse_jacobian_cache(ad::AbstractADType, sd::AbstractSparsityDetection, f!, fx, x)
```

基盤となるADバックエンド`ad`、スパース検出アルゴリズム`sd`、関数`f`、および入力`x`を受け取り、ヤコビ行列を計算するために使用できるキャッシュオブジェクトを返します。

`fx`が指定されていない場合、`f(x)`を呼び出すことで計算されます。

## 戻り値

タイプ`AbstractMaybeSparseJacobianCache`のヤコビ行列を計算するためのキャッシュ。
