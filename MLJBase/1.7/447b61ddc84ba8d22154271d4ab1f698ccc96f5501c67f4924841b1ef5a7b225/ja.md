```
partition(X, fractions...;
          shuffle=nothing,
          rng=Random.GLOBAL_RNG,
          stratify=nothing,
          multi=false)
```

ベクトル、行列、またはテーブル `X` を、垂直に連結すると `X` になる同じ型のオブジェクトのタプルに分割します。返される値の各コンポーネントの行数は、`length(nrows(X))` の対応する `fractions` によって決定されます。有効な分数は、合計が1未満の0と1の間の浮動小数点数です。最後の分数は提供されず、前の分数から推測されます。

複数のオブジェクトの同期分割には、`multi=true` オプションを使用します。

```julia-repl
julia> partition(1:1000, 0.8)
([1,...,800], [801,...,1000])

julia> partition(1:1000, 0.2, 0.7)
([1,...,200], [201,...,900], [901,...,1000])

julia> partition(reshape(1:10, 5, 2), 0.2, 0.4)
([1 6], [2 7; 3 8], [4 9; 5 10])

julia> X, y = make_blobs() # テーブルとベクトル
julia> Xtrain, Xtest = partition(X, 0.8, stratify=y)
```

複数のオブジェクトの同期分割の例は次のとおりです：

```julia-repl
julia> (Xtrain, Xtest), (ytrain, ytest) = partition((X, y), 0.8, rng=123, multi=true)
```

## キーワード

  * `shuffle=nothing`: `true` に設定すると、分数を取得する前に行をシャッフルします。
  * `rng=Random.GLOBAL_RNG`: 使用する乱数生成器を指定します。整数のシードを指定できます。指定された場合、`shuffle === nothing` は真と解釈されます。
  * `stratify=nothing`: ベクトルが指定されると、パーティションは指定されたベクトルの層別化に一致します。その場合、`shuffle` は `false` にはできません。
  * `multi=false`: `true` の場合、`X` は共通の長さを持つオブジェクトの `tuple` であることが期待され、それぞれが同じ指定された `fractions` *および* 同じ行のシャッフルを使用して個別に分割されます。パーティションのタプル（タプルのタプル）を返します。
