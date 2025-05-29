```
TimeArray{T,N,D<:TimeType,A<:AbstractArray{T,N}} <: AbstractTimeSeries{T,N,D}
```

# コンストラクタ

```
TimeArray(timestamp, values[, colnames, meta = nothing])
TimeArray(ta::TimeArray; timestamp, values, colnames, meta)
TimeArray(data::NamedTuple; timestamp, meta = nothing)
TimeArray(table; timestamp::Symbol, timeparser::Callable = identity)
```

2番目のコンストラクタは、新しいフィールドを持つ新しい `TimeArray` を生成します。変更されていないフィールドは共有され、基になる配列のコピーはありません。

3番目のコンストラクタは、`NamedTuple` から `TimeArray` を構築します。

# 引数

  * `timestamp::AbstractVector{<:TimeType}`: ソートされたタイムスタンプのベクター、
  * `timestamp::Symbol`: ソーステーブルからの時間インデックスの列名。コンストラクタは Tables.jl パッケージの統合に使用されます。
  * `values::AbstractArray`: データベクターまたは行列。その行数は `timestamp` の長さと一致する必要があります。
  * `colnames::Vector{Symbol}`: 列名。その長さは `values` の列と一致する必要があります。
  * `meta::Any`: ユーザー定義のメタデータ。
  * `timeparser::Callable`: ソース時間インデックスを変換するためのマッピング関数。例えば、`Dates.unix2datetime` は一般的なケースです。

# 例

```
data = (datetime = [DateTime(2018, 11, 21, 12, 0), DateTime(2018, 11, 21, 13, 0)],
        col1 = [10.2, 11.2],
        col2 = [20.2, 21.2],
        col3 = [30.2, 31.2])
ta = TimeArray(data; timestamp = :datetime, meta = "Example")
```
