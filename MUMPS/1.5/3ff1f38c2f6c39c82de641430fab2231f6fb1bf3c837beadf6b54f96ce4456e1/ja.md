```
solve!(mumps;transposed=false)
```

`Mumps`オブジェクト`mumps`に登録されたシステムを解きます。行列と右辺は、事前に`associate_matrix()`および`associate_rhs()`で登録されている必要があります。オプションのキーワード引数`transposed`は、ユーザーが前方または転置システムを解きたいかどうかを示します。解は内部に保存され、`get_solution()`で取得する必要があります。
