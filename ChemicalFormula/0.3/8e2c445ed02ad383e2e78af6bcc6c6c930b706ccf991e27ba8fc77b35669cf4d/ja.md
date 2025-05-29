```
latex(formula, includecharge=true, form="formula")
```

LaTeXで書かれた式をmhchemパッケージを使用して提供します。`includecharge`は電子の電荷を表示するかどうかを決定し、デフォルトは`true`です。`form`は`"formula"`（`Formula`オブジェクトを構築するために与えられた`formula`）、`"hill"`または`"hillformula"`（ヒル表記用）、または`"sum"`または`"sumformula"`（圧縮された和式用）のいずれかでなければならず、デフォルトは`"formula"`です。
