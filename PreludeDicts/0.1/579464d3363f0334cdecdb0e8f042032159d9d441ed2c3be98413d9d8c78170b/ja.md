```
modify!(f, dict, key) -> y
```

`key`に対する`dict`のスロットを、`nothing`または`key′ => value`を`nothing`、`Some(value)`、[`Keep(_)`](@ref Keep)、または[`Delete(_)`](@ref Delete)にマッピングする`f`を使用して修正します。

`f`は2つのタイプの引数を取ります：

  * `nothing`：`key`に関連付けられたスロットが空いていることを示します。
  * `key′ => value`（または類似のペアのような値）：`key`に関連付けられたスロットが`key′ => value`を格納していることを示します。

`f`は以下の値を返すことができます：

  * `nothing`または`Delete(x)`：`key`に関連付けられた値を削除する必要があることを示します。`Delete`は、`f`で計算された値を返すのに便利です。
  * `Some(value)`：`key`に関連付けられたスロットの新しい`value`を設定します。
  * `Keep(x)`：`key`に関連するスロットを修正しないことを示します。`f`で計算された値を返すのに便利です。

# 拡張ヘルプ

## 例

```jldoctest PreludeDicts0
julia> using PreludeDicts

julia> inc!(dict, key) = modify!(dict, key) do slot
           if slot === nothing
               Some(1)
           else
               Some(last(slot) + 1)
           end
       end;

julia> dict = Dict(:a => 111);

julia> inc!(dict, :a)
Some(112)

julia> inc!(dict, :b)
Some(1)

julia> dict == Dict(:a => 112, :b => 1)
true
```
