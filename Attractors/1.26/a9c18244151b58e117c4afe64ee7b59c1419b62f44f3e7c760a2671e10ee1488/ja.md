```
RecurrencesFindAndMatch <: GlobalContinuationAlgorithm
RecurrencesFindAndMatch(mapper::AttractorsViaRecurrences; kwargs...)
```

[`global_continuation`](@ref)に基づくメソッドで、[Datseris2023](@cite)のように、アトラクタを見つけるための再帰アルゴリズム（[`AttractorsViaRecurrences`](@ref)）に基づいており、その後、状態空間距離に従ってそれらをマッチングします。

## キーワード引数

  * `distance = Centroid(), threshold = Inf`: [`MatchBySSSetDistance`](@ref)に渡されます。
  * `seeds_from_attractor`: アトラクタを入力として受け取り、次のパラメータスライスのためにアトラクタからシードされる初期条件のイテレータを返す関数です。デフォルトでは、アトラクタ上の最初に保存されたポイントのみをサンプリングします。

## 説明

`RecurrencesFindAndMatch`はラッパータイプです。これは[`AttractorSeedContinueMatch`](@ref)によって一般化されています。後方互換性のため、また[Datseris2023](@cite)で開発された元のアルゴリズムへの明確な参照を持つために、依然としてエクスポートされています。

`RecurrencesFindAndMatch`のソースコードは単純です。与えられたマッパーを受け取り、[`MatchBySSSetDistance`](@ref)を初期化し、`seeds_from_attractor`と共に[`AttractorSeedContinueMatch`](@ref)インスタンスを作成します。これは、アトラクタが再帰アルゴリズム[`AttractorsViaRecurrences`](@ref)を使用して見つけられ、その後、状態空間における距離でマッチングされるという[Datseris2023](@cite)で説明されたプロセスです。 ```
