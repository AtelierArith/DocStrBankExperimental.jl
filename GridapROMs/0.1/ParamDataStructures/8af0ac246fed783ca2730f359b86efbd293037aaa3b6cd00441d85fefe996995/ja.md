```
struct Realization{P<:AbstractVector} <: AbstractRealization
  params::P
end
```

標準的なパラメトリック実現を表します。すなわち、与えられたパラメータ空間から抽出されたサンプルです。フィールド `params` は最も一般的にはベクトルのベクトルです。パラメータがスカラーの場合でも、長さ1のベクトルのベクトルとして定義する必要があります。言い換えれば、`params` が数のベクトルである場合は、`params` が1つのベクトルのベクトルである場合と同様に扱います。
