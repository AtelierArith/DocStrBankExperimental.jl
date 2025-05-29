```
RecordEntry{T} <: RecordAction
```

特定のフィールドエントリのタイプ {T} をイテレート中に記録します

# フィールド

  * `recorded_values` : 記録されたイテレート
  * `field`           : [`AbstractManoptSolverState`](@ref) 内でアクセスできるシンボル

# コンストラクタ

```
RecordEntry(::T, f::Symbol)
RecordEntry(T::DataType, f::Symbol)
```

状態フィールド `f` を記録するためにレコードアクションを初期化し、`recorded_values` を要素タイプ `T` のベクターとして初期化します。

# 例

  * `RecordEntry(rand(M), :q)` は、いくつかの状態 `s.q` に保存された `M` からのポイントを記録します
  * `RecordEntry(SVDMPoint, :p)` は、[`SVDMPoint`](@extref `Manifolds.SVDMPoint`) のタイプの値を取るフィールド `s.p` を記録します。
