```
doubledescription(h::HRepresentation; tol)
```

`h`によって表される多面体のV-表現をDouble-Descriptionアルゴリズム[MRTT53, FP96]を使用して計算します。結果の表現に含まれる点、光線、直線のリストを維持し、各半空間に対応する超平面内でそれらの交差を追加し、[`Polyhedra.add_intersection!`](@ref)を使用します。結果のV-表現には冗長性がありません。

```
doubledescription(V::VRepresentation)
```

`v`によって表される多面体のH-表現をDouble-Descriptionアルゴリズム[MRTT53, FP96]を使用して計算します。現在、これは同次化によって円錐のV-表現に持ち上げることにフォールバックし、双対円錐のH-表現として解釈されるため、`doubledescription(::HRepresentation)`に依存することができます。

[MRTT53] Motzkin, T. S., Raiffa, H., Thompson, G. L. and Thrall, R. M. The double description method *Contribution to the Theory of Games*, *Princeton University Press*, **1953**

[FP96] Fukuda, K. and Prodon, A. Double description method revisited *Combinatorics and computer science*, *Springer*, **1996**, 91-111
