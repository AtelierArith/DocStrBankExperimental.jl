`StaticLengthSortOblivious{n,Opt}()`を使用して、静的に知られた長さのコレクションに適応したソートアルゴリズムを選択します。このアルゴリズムは、オブリビアスマージソートであり、オプションで`OptimalSortingNetworks`パッケージのソートネットワークを使用してベースケースを高速化します。このソートは安定ではありません。

値`n`は、非負整数でなければならず、`OptimalSortingNetworks`からのハードコーディングされたソートネットワークを使用して、`OptimalSortingNetworks`がサポートする場合に、`n`未満の要素を含むコレクションをソートすることを示します。すべてのコレクションに対して`OptimalSortingNetworks`がサポートされている場合、例えば大きな`n`、`100`を選択してソートネットワークを使用します。

型`Opt`は、[`SmallDepth`](@ref)または[`SmallSize`](@ref)である可能性があります。
