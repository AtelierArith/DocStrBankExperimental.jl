```
deflation(f::MPolyRingElem{T}) where T <: RingElement
```

多項式 $f$ の指数に対するデフレーションパラメータを計算します。これは整数の配列のペアであり、最初の配列（シフト）は多項式の各変数の最小指数を示し、2番目の配列（デフレーション）はシフトを引いた後のすべての指数の gcd を示します。これも変数ごとに行われます。この機能は gcd によって使用され（因数分解アルゴリズムでも使用可能です）。
