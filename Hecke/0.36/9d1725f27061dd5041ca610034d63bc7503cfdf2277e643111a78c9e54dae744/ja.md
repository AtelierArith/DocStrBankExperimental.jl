```
conjugates_log(a::AbsSimpleNumFieldElem, C::qAdicConj, n::Int = 10; flat::Bool = false, all:Bool = true) -> []
conjugates_log(a::FacElem{AbsSimpleNumFieldElem, AbsSimpleNumField}, C::qAdicConj, n::Int = 10; flat::Bool = false, all:Bool = true) -> []
```

$$
a
$$

の$q$-adic共役の対数の配列を返します：$p Z_K = \prod P_i$は、$a$の親の最大順序$Z_K$のためのものです。次に、$K \otimes Q_p = \prod K_{P_i}$です。各$P_i$について、$Q_p$の$q$-adic（非分岐）拡張$K_{P_i}$が計算されます。$a$は$\deg P_i = \deg K_{P_i}$個の共役を$K_{P_i}$に持ちます。`all = true`かつ`flat = false`の場合、すべての$n$個の共役の対数が返されます。`all = false`の場合、各$P_i$について共役の対数は1つだけが返され、他のものは自己同型（フロベニウス）を使用して計算できます。`flat = true`の場合、共役の代わりに$p$-adic係数のみが返されます。
