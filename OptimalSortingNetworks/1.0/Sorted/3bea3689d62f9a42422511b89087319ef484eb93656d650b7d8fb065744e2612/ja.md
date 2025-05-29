比較/交換要素を構築するためのヘルパー関数で、[`sorted`](@ref)で使用するのが簡単になります。

引数:

1. ソートされるコレクションの型を表すオプションの位置引数 `T`。
2. `by` 変換を指定するためのオプションのキーワード引数 `by`。デフォルトは `default_minmax_by(T)` です。詳細は [`default_minmax_by`](@ref) を参照してください。
3. `less` 比較述語を指定するためのオプションのキーワード引数 `less`。デフォルトは `default_minmax_less(T)` です。詳細は [`default_minmax_less`](@ref) を参照してください。
