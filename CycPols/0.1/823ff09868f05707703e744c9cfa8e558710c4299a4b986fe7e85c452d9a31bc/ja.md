`CycPol`は内部的にフィールドを持つ`struct`です：

`.coeff`:  通常は`Cyc`または`Pol`の係数。`Pol`の場合、任意の`Pol`を`CycPol`として表現できるため、時々便利です。

`.valuation`: `Int`。

`.v`: `ModuleElt{Rational{Int},Int}`で、ペア`r=>m`は`Root1(;r=r)`の根としての重複度`m`を示します。

したがって、`CycPol(coeff,val,v)`は`coeff*q^val*prod((q-Root1(;r=r))^m for (r,m) in v)`を表します。
