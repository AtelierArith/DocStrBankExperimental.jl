```
Wadd, Hadd, S = gsvdrecover(X, W0, H0, kadd, f)
```

NMFによる磨きをかけずに`W`と`H`のコンポーネントを拡張します。

出力:

`Wadd`: 拡張されたNMFソリューション

`Hadd`: 拡張されたNMFソリューション

`S`: `kadd`で拡張されたコンポーネントの一般化された特異値

引数:

`X`: 非負の2Dデータ行列

`W0`: NMFソリューション

`H0`: NMFソリューション

`kadd`: 新しいコンポーネントの数

`f`: `X`のSVD（またはトランケートSVD）
