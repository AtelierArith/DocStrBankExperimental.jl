```
se = ExtendedStateSpace(s::AbstractStateSpace; kwargs...)
```

通常の状態空間オブジェクトから `ExtendedStateSpace` への変換は、デフォルトで以下のシステムを作成します。

$$
\begin{bmatrix}
    A & B & B \\
    C & D & D \\
    C & D & D
\end{bmatrix}
$$

すなわち、システムとパフォーマンスのマッピングは同一であり、`system_mapping(se) == performance_mapping(se) == s` です。ただし、すべての行列 `B1, B2, C1, C2; D11, D12, D21, D22` は、対応するキーワード引数によってオーバーライド可能です。この場合、制御出力は測定出力と同じです。

関連: `se = convert(ExtendedStateSpace, s::StateSpace)` は、`ss(se) == s` となるように、w->z から空の `performance_mapping` を持つ `ExtendedStateSpace` を生成します。
