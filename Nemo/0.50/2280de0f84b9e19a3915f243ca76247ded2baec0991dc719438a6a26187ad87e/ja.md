```
lindep(A::Vector{AcbFieldElem}, bits::Int)
```

配列 $A$ のエントリの小さな線形結合を見つけます（LLLを使用）。エントリは、LLLで使用するために実部と虚部を整数に切り捨てる前に、指定されたビット数でスケーリングされます。この関数は、複素数のリスト間の線形依存性を見つけるために使用できます。アルゴリズムはヒューリスティックであり、線形結合を表すNemo整数の配列を返します。
