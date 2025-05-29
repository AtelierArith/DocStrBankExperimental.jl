```
fit(SubspaceLDA, X, y; normalize=true)
```

与えられたデータセット `X` と対応するラベル `y` に対して、LDAモデルのサブスペース投影を $\mathbf{S}_w^*$ と $\mathbf{S}_b^*$ の同等物を使用して適合させます。

注意: サブスペースLDAは、`normalize` キーワードを介してLDAの正規化バージョンもサポートしています。
