このモジュールは、GAPからの組合せ論および基本的な数論関数のJuliaポートとして始まりました。`Combinatorics.jl`との比較については、以下のコメントを参照してください。唯一の依存関係は`Primes`パッケージです。

エクスポートされる関数のリストは次のとおりです：

古典的な列挙：

[`combinations`](@ref), [`arrangements`](@ref), [`permutations`](@ref), [`partitions`](@ref), [`partition_tuples`](@ref), [`compositions`](@ref), [`multisets`](@ref)

列挙を計算せずにカウントするための関数：

`ncombinations`, `narrangements`, `npartitions`, `npartition_tuples`, `ncompositions`, `nmultisets`

部分集合と順列に関するいくつかの関数：

[`lcm_partitions`](@ref), [`gcd_partitions`](@ref), [`conjugate_partition`](@ref), [`dominates`](@ref), [`tableaux`](@ref), [`robinson_schensted`](@ref)

カウント関数：

[`bell`](@ref), [`stirling1`](@ref), [`stirling2`](@ref), [`catalan`](@ref), [`bernoulli`](@ref)

数論

[`prime_residues`](@ref), [`primitiveroot`](@ref), [`moebius`](@ref)

Juliaにまだ（？）ないいくつかの構造的操作：

[`groupby`](@ref), [`tally`](@ref), [`tally_sorted`](@ref), [`collectby`](@ref), [`unique_sorted!`](@ref), [`union_sorted`](@ref), [`intersect_sorted`](@ref)

行列ブロック：

[`blocks`](@ref), [`diagblocks`](@ref)

個々のドキュメント文字列を見て楽しんでください（フィードバックは歓迎です）。

このモジュールのほとんどを書いた後、かなりの重複がある`Combinatorics`パッケージに気付きました。しかし、これら2つのパッケージの間にはいくつかの不一致があり、`Combinatorics`は私にとって簡単に使えるものではありません：

  * 私は、`Combinatorics`がハッシュを使用するアルゴリズムでソートをよく使用します。したがって、アルゴリズムは常に同じ型に適用されるわけではありません（ソートはしばしば速いです）。いくつかのアルゴリズムでは、キーワードを使用してハッシュのバリアントを選択できます。ここで、ハッシュ可能とは`hash`メソッドを持つ型を指し、ソート可能とは`isless`メソッドを持つ型を指します。
  * `Combinatorics.combinations`は空の部分集合を含みません。
  * 列挙をリストとして返す関数には小文字を使用し、イテレータにはキャメルケースを使用します。多くの列挙には両方のバリアントがあります。`Combinatorics`には列挙のための1つのバリアントしかありませんが、それはしばしば小文字のイテレータです。
  * `Combinatorics`は列挙が少ないです。

あまり根本的ではない不一致は名前に関するものです。しかし、`Combinatorics`の著者との議論を歓迎し、両方のパッケージがこの点でより互換性を持つようにできるかどうかを見たいと思います。
