```
read_libsvm(filepath::String; has_query=false)
read_libsvm(raw::Vector{UInt8}; has_query=false)
```

LIBSVM形式のデータをファイルまたは生のバイトベクターから読み込み、特徴行列、ターゲットラベル、およびオプションでクエリエントリを含むタプルとして返します。

# 引数

  * `filepath::String`: LIBSVM形式のデータを含むファイルへのパス。`filepath`または`raw`のいずれか一方のみを提供する必要があります。
  * `raw::Vector{UInt8}`: LIBSVM形式のデータを含む生のバイトのベクター。`filepath`または`raw`のいずれか一方のみを提供する必要があります。
  * `has_query::Bool=false`: データにクエリエントリが含まれているかどうかを示すブールフラグ。

# 戻り値

  * `has_query`が`false`の場合、タプル`(x, y)`を返します。ここで、

      * `x::Matrix{Float64}`: 各行がデータポイントを表し、各列が特徴を表す密な`Float64`行列としての特徴行列。
      * `y::Vector{Float64}`: 密な`Float64`のベクターとしてのターゲットラベル。
  * `has_query`が`true`の場合、タプル`(x, y, q)`を返します。ここで、

      * `x::Matrix{Float64}`: 密な`Float64`行列としての特徴行列。
      * `y::Vector{Float64}`: 密な`Float64`のベクターとしてのターゲットラベル。
      * `q::Vector{Int}`: 密な`Int`のベクターとしてのクエリエントリ。
