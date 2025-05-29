```
kernel_lattice(L::ZZLat, f::MatElem;
               ambient_representation::Bool = true) -> ZZLat
```

与えられた $\mathbf{Z}$-格子 $L$ と $L$ の自己準同型を誘導する行列 $f$ に対して、$\ker(f)$ を $L$ の部分格子として返します。

`ambient_representation` が `true`（デフォルト）である場合、自己準同型は $L$ の周囲空間に関して表現されます。そうでない場合、自己準同型は $L$ の基底に関して表現されます。
