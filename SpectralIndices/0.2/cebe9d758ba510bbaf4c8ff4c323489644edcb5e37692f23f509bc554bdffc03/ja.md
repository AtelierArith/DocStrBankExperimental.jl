```
compute_index(index::String, params::Dict=Dict(), online::Bool=false; kwargs...) -> Any
```

指定されたインデックス名、パラメータ、およびオプションのキーワード引数に基づいて、事前定義されたリストから1つ以上のスペクトルインデックスを計算します。

# パラメータ

  * `index`: 計算するスペクトルインデックスの名前またはインデックス名のリスト。
  * `params`: （オプション）計算の入力として使用されるパラメータの辞書。提供されない場合、パラメータはキーワード引数を使用して渡すことができます。
  * `online`: （オプション）最新のインデックスリストをオンラインで取得するかどうかを示すフラグ。
  * `kwargs`: 計算の入力として使用される追加のパラメータで、キーワードペアとして提供されます。

# 戻り値

  * 計算されたスペクトルインデックス。戻り値の型は入力パラメータに依存します。

# 例

```julia-repl
julia> compute_index("NDVI"; N=0.643, R=0.175)

```

```julia-repl
julia> compute_index("NDVI"; N=fill(0.643, (5, 5)), R=fill(0.175, (5, 5)))

```

```julia-repl
julia> compute_index("NDVI"; N=fill(0.643, 5), R=fill(0.175, 5))

```

```julia-repl
julia> compute_index(["NDVI", "SAVI"]; N=fill(0.643, 5), R=fill(0.175, 5), L=fill(0.5, 5))

```

```julia-repl
julia> compute_index(["NDVI", "SAVI"]; N=0.643, R=0.175, L=0.5)

```

```julia-repl
julia> compute_index(
           ["NDVI", "SAVI"]; N=fill(0.643, (5, 5)), R=fill(0.175, (5, 5)), L=fill(0.5, (5, 5))
       )

```
