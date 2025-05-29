```
substitute_latex(md::AbstractString, scale::Number, im_dir; extra_packages="")::String
```

Markdown文字列`md`内のLaTeXを置き換えます。LaTeX画像は`im_dir/<h>.svg`に配置され、ここで`h`は数式に対して計算されたハッシュです。画像サイズの調整は`scale`を設定することで可能です。

ハッシュを使用する利点は、ブラウザが数式ごとに1つの画像のみをダウンロードすることです。
