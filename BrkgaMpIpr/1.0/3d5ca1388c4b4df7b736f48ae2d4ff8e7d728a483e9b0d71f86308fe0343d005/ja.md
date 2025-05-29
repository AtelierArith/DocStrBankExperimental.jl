```
abstract type AbstractInstance
```

デコーダに提供される外部データのための必要なインターフェース。問題の定義とデータは**必ず**AbstractInstanceのサブタイプでなければなりません。例えば、

```julia
mutable struct TSPInstance <: AbstractInstance
    num_cities::Int64
    distances::Array{Float64}
end
```

は、都市の数とそれらの間の距離の行列を定義する巡回セールスマン問題のインスタンスタイプを表します。
