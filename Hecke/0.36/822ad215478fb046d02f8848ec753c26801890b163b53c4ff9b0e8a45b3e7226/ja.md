```
pseudo_hnf(P::PMat)
```

$$
P
$$

をCohenによって定義された擬似エルミート形式に変換します。基本的に、$P$の行列部分は上三角行列になり、オフ対角要素に対していくつかの技術的正規化が行われます。この操作はモジュールを保持します。

オプションの第二引数として、エシロン形式の望ましい形状を示すシンボルを指定できます。可能な値は`：upperright`（デフォルト）と`：lowerleft`です。
