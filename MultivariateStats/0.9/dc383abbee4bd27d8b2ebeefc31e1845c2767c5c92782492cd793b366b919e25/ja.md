```
fit(SubspaceLDA, X, labels; normalize=true)
```

LDAモデルの部分空間射影を、$\mathbf{S}_w^*$と$\mathbf{S}_b^*$の同等物を使用して適合させます。

注：部分空間LDAは、`normalize`キーワードを介してLDAの正規化バージョンもサポートしています。
