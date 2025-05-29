```
stroud_quad_nodes(elem::AbstractElemShape,N)
```

ストラウド型の数値積分ノードと重みを返します。これは(N+1)点のガウス-ヤコビルールのテンソル積から構成されています。次数2Nの多項式に対して正確です。
