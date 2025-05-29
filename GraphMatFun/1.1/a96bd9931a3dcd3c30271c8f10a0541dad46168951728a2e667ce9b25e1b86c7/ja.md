```
(graph,crefs)=graph_degopt(k;T=ComplexF64,input=:A)
(graph,crefs)=graph_degopt(x,z;input=:A)
(graph,crefs)=graph_degopt(d::Degopt;input=:A)
```

固定された乗算の数に対して、次数最適な多項式に対応します。

```
B1=A
B2=(x *I+x *A)(x *I+x *A)
B3=(x *I+x *A+x*B2)(x *I+x *A+x *B2)
 ..
```

および

```
Out=z*I+z*A1+z*B2+z*B3+z*B4...
```

`x`の値は引数`x`に与えられ、これは各和の要素を含む`Vector{Tuple{Vector,Vector}}`です。`z`ベクトルは出力を形成する要素を含み、`input`は上記の行列Aの名前を決定します。係数の代わりにパラメータ`k`が供給されると、すべての係数は1に設定されます。一般的な再帰は、以下の文献の(9)に示されています。

**参考文献**

1. P. Bader, S. Blanes, and F. Casas, "Computing the matrix exponential with an optimized Taylor polynomial approximation", Mathematics, 7(12), 2019. DOI: [10.3390/math7121174](https://doi.org/10.3390/math7121174)
