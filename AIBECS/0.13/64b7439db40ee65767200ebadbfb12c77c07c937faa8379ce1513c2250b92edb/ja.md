```
bijector(T::AbstractParameters [, k::Symbol])
```

パラメータの変数変換のための関数を返します。

この関数は、事前分布のサポート/ドメインから ℝⁿ への全単射です。Bijectors.jl パッケージからのものです。特定のパラメータシンボルを指定することで、そのパラメータのバイジェクタを取得できます。
