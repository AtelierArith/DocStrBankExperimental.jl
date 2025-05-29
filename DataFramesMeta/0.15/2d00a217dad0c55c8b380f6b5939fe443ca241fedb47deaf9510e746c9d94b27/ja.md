```
groupby(df, args...)
```

データフレームを列でグループ化します。以下のエイリアスです。

```
groupby(df, Cols(args...))
```

ただし、いくつかの便利な機能があります。

## 詳細

`@groupby` は変換を行わず、新しい列の生成を許可しません。新しい列の生成は `@groupby` が呼ばれる前に行う必要があります。

`@groupby` は `Symbol` と `String` の入力を混在させることを許可しており、`@groupby df :A "B"` がサポートされています。

引数はエスケープされず、列選択のための DataFramesMeta.jl ルール、例えばエスケープのための `$` は適用されません。

## 例

```julia-repl
julia> df = DataFrame(A = [1, 1], B = [3, 4], C = [6, 6]);
julia> @groupby df :A;
julia> @groupby df :A :B;
julia> @groupby df [:A, :B];
julia> @groupby df :A [:B, :C];
```
