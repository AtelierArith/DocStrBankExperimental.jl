```
StructuredArray([S = IndexCartesian,] func, args...) -> A
StructuredArray{T}([S = IndexCartesian,] func, args...) -> A
StructuredArray{T,N}([S = IndexCartesian,] func, args...) -> A
StructuredArray{T,N,S}(func, args...) -> A
```

`A`という`N`次元配列を構築し、インデックス`i`での値は`func(i)`として計算され、形状は`args...`で指定されます。ストレージ要件は通常の配列の`O(length(A))`ではなく`O(1)`です。オプションのパラメータ`T`、`N`、および`S`は、要素の型、次元数、および配列のインデックススタイルの型を指定するためのものです。引数として指定された場合、型パラメータとしてではなく、`S`は`IndexStyle`のインスタンスであることもできます。

関数`func`は、基本メソッド`getindex`で指定されたインデックスで呼び出されます：インデックススタイルが`IndexCartesian`（デフォルト）の場合、関数`func`は`N`個の整数引数（`Vararg{Int,N}`）で呼び出されます；`S`が`IndexLinear`の場合、関数`func`は単一の整数引数（`Int`）で呼び出されます。

例えば、サイズ`m×n`の下三角行列の構造は次のように与えられます：

```
StructuredArray((i,j) -> (i ≥ j), m, n)
```

ただし、行列のサイズに関わらず、一定の小さなストレージ要件があります。

呼び出し可能なオブジェクト`func`は*純粋関数*でない場合もありますが、その戻り値の型は安定しており、構造体配列は不変と見なされるため、`A[i] = x`のような文は実装されていません。コンストラクタへの呼び出しでパラメータ`T`が指定されていない場合、構造体配列の要素の型は単位インデックスに`func`を適用することによって推論されます。
