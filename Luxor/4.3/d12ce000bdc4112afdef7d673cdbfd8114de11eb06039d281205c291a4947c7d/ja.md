```
tidysvg(fname)
```

`fname` にある SVG 画像を読み込み、修正されたグリフ名で `fname-tidy.svg` というファイルに書き込みます。

修正されたファイルの名前を返します。

SVG 画像はテキストのために「名前付き定義」を使用しており、これがブラウザやノートブックで使用されると問題を引き起こします。詳細については [この github issue](https://github.com/jupyter/notebook/issues/333) を参照してください。

手間のかかる回避策は、要素の名前を変更することです。
