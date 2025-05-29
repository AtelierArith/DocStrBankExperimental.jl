```
Barycentric(node, value, weight, wf=value .* weight; stats=missing)
```

`Barycentric` 有理関数を構築します。

# 引数

  * `node::Vector`: 補間ノード
  * `value::Vector`: 補間ノードでの値
  * `weight::Vector`: バリセントリック重み

# キーワード

  * `wf::Vector = value .* weight`: 重みと値の積

# 戻り値

  * `::Barycentric`: バリセントリック有理補間関数

# 例

```jldoctest
julia> r = Barycentric([1, 2, 3], [1, 2, 3], [1/2, -1, 1/2])
Barycentric function with 3 nodes and values:
    1.0=>1.0,  2.0=>2.0,  3.0=>3.0

julia> r(1.5)
1.5
```
