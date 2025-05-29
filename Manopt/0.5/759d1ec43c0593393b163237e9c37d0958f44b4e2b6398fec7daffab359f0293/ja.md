```
StoreStateAction <: AbstractStateAction
```

[`AbstractStateAction`](@ref)の内部ストレージは、[`AbstractManoptSolverState`](@ref)からのフィールドのタプルを格納します。

このファンクタは、反復中に呼び出される関数の通常のインターフェースを持ち、`(p, s, k)`に作用します。ここで、`p`は[`AbstractManoptProblem`](@ref)、`s`は[`AbstractManoptSolverState`](@ref)、`k`は現在の反復です。

# フィールド

  * `values`:        特定の`Symbols`に基づいて中間値を格納する辞書
  * `keys`:          `AbstractManoptSolverState`のフィールドを参照する`Symbols`の`Vector`
  * `point_values`:  `StoreStateAction`に格納される多様体上の点の可変値の`NamedTuple`。多様体は後で`update_storage!`に渡される`AbstractManoptProblem`によって決定されます。
  * `point_init`:    一致するキーを持つ`point_values`内の点がすでに値に初期化されているかどうかを示すブール値の`NamedTuple`。これがfalseの場合、ベクター`keys`内のキーに対して格納されていない一般的な値に対応します。
  * `vector_values`: 多様体上の接ベクトルの可変値の`NamedTuple`で、`StoreStateAction`に格納されます。多様体は後で`update_storage!`に渡される`AbstractManoptProblem`によって決定されます。ベクトルがどの点で接しているかは指定されていませんが、ストレージには影響しないはずです。
  * `vector_init`:   一致するキーを持つ`vector_values`内の接ベクトルがすでに値に初期化されているかどうかを示すブール値の`NamedTuple`。これがfalseの場合、ベクター`keys`内のキーに対して格納されていない一般的な値に対応します。
  * `once`:          各反復ごとに内部値を一度だけ更新するかどうか
  * `lastStored`:    この`AbstractStateAction`が呼び出された最後の反復（`once`を決定するため）

一般的なストレージを扱うには、`get_storage`と`has_storage`を`Symbol`としてのキーで使用します。点のストレージには`PointStorageKey`を使用します。接ベクトルのストレージには`VectorStorageKey`を使用します。点と接ベクトルのストレージは、より効率的になるように最適化されています。

# コンストラクタ

StoreStateAction(s::Vector{Symbol})

これは、`s`をキーワード`store_fields`に提供するのと同等ですが、ここでは構築に多様体は必要ありません。

```
StoreStateAction(M)
```

## キーワード引数

  * `store_fields` (`Symbol[]`)
  * `store_points` (`Symbol[]`)
  * `store_vectors` (`Symbol[]`)

それぞれ状態のフィールド（小文字のシンボル）または意味的なもの（大文字）を参照するシンボルのベクターとして。

  * `p_init` (`rand(M)`) ただし、これは数値ではなく（可変可能な）配列であることを確認してください。
  * `X_init` (`zero_vector(M, p_init)`)

は、点とベクトルのストレージを初期化するために使用されます。他のタイプ（デフォルト以外）を`M`上の点/ベクトルに使用する場合は、これらを変更してください。

  * `once` (`true`) 各反復ごとに内部ストレージを一度だけ更新するか、すべての更新呼び出しで更新するかどうか
