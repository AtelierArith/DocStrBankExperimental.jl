```
SOS1
```

SOS1（特別順序集合タイプ1）オブジェクトは、ベクトル `x` を制約するために使用でき、最大1つの変数が非ゼロの値を取ることができ、他のすべては0であるセットです。指定された場合、`weights` は変数の順序を誘導します。そのため、ユニークな値である必要があります。セット内の *k* 番目の要素は、`weights` の *k* 番目の重みと対応します。SOS制約とその潜在的な使用法の説明については、[こちら](http://lpsolve.sourceforge.net/5.5/SOS.htm)を参照してください。これは `MathOptInterface.SOS1` セットのショートカットです。
