```
Image <: SingleGridRenderer

Image(f=identity; scheme=ObjectScheme(), zerocolor=nothing, maskcolor=nothing)
```

出力グリッドをカラースキームに変換します。

# 引数

  * `f`: グリッドから `Real` または `RGB` への値を変換する関数。`Real` は minval/maxval によってスケーリングされ、`scheme` によって色付けされます。`RGB` は出力に直接使用されます。これは複雑なオブジェクトのグリッドに便利ですが、数値には必要ありません。デフォルトは `identity` です。

# キーワード

  * `scheme`: ColorSchemes.jl のカラースキーム、[`ObjectScheme`](@ref) または `Base.get(obj, val)` を定義し、`Color` または `ARGB32(val)` を使用して `Color` に変換できる値を返すオブジェクト。
  * `zerocolor`: 値がゼロのときに使用する `Col`、または無視するための `nothing`。
  * `maskcolor`: セルがマスクされているときに使用する `Color`、または無視するための `nothing`。
