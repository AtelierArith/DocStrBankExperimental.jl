```
MatrixAlgebraKit.findtruncated(values::AbstractVector, strategy::TruncationStrategy)
```

分解のスペクトルの切り捨てられた値を見つけるための汎用インターフェースで、`strategy`に基づいています。出力は、保持する値を指定するインデックスのコレクションである必要があります。`MatrixAlgebraKit.findtruncated`は、切り捨てを実行するために[`truncate!`](@ref)のデフォルト実装内で使用されます。値がソートされているとは仮定しません。絶対値で逆にソートされていることを仮定するバージョン（SVDの標準ケース）は、[`MatrixAlgebraKit.findtruncated_sorted`](@ref)を参照してください。
