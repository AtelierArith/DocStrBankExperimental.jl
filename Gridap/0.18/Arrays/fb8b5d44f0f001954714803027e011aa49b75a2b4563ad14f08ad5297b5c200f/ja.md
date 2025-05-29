```
lazy_map(f,a::AbstractArray...) -> AbstractArray
```

`Map`（または`Function`）`f`を配列`a`のエントリに適用します（[`Map`](@ref)の定義を参照）。

結果として得られる配列`r`は、`r[i]`が`evaluate(f,ai...)`に等しく、ここで`ai`は配列`a`の`i`-thエントリを含むタプルです（詳細については関数[`evaluate`](@ref)を参照）。言い換えれば、結果の配列は数値的に次のように等価です：

```
map( (x...)->evaluate(f,x...), a...)
```

# 例

関数をマッピングとして使用する

```jldoctest
using Gridap.Arrays

a = collect(0:5)
b = collect(10:15)

c = lazy_map(+,a,b)

println(c)

# 出力
[10, 12, 14, 16, 18, 20]
```

ユーザー定義のマッピングを使用する

```jldoctest
using Gridap.Arrays
import Gridap.Arrays: evaluate!

a = collect(0:5)
b = collect(10:15)

struct MySum <: Map end

evaluate!(cache,::MySum,x,y) = x + y

k = MySum()

c = lazy_map(k,a,b)

println(c)

# 出力
[10, 12, 14, 16, 18, 20]
```
