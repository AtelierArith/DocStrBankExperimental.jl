```
grouponly([by], [f], iter)
```

`iter`のユニークな要素`x`を`by(x)`でグループ化し、値を`f(x)`にマッピングする辞書を返します。`by`と`f`はデフォルトで恒等関数になります。

これは`only.(group(by, f, iter))`の最適化された同等物であり、`Dictionary(by.(iter), f.(iter))`に似ています。
