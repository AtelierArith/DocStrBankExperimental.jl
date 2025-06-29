```
is_local_norm(mkK::Map, a::AbsSimpleNumFieldElem) -> Bool
```

`mkK : k \to K` を数体の写像（埋め込み）とします。    

$$
a
$$

がその写像に暗黙的に含まれる相対拡張のローカルノルムであるかどうかをテストします。すなわち、$k$ の素イデアル $p$ に対して、$Q_i$ をその上にある素数とします。$a$ がローカルノルムであるためには、$Q_i$ での完備化において $b_i$ が存在し、$\prod N(b_i) = q$ となる必要があります。ここで、ノルム $N$ は $Q_i$ での完備化から $p$ での完備化へのものです。  
