```
FixedRectangularBinning <: AbstractBinning
FixedRectangularBinning(ranges::Tuple{<:AbstractRange...}, precise = false)
```

状態空間の矩形ボックス分割で、各次元に沿った分割は各範囲 `ranges` によって明示的に与えられます。これは `AbstractRange` サブタイプのタプルです。通常、各範囲は `range` Base 関数の出力であり、例えば `ranges = (0:0.1:1, range(0, 1; length = 101), range(2.1, 3.2; step = 0.33))` のようになります。すべての範囲はソートされている必要があります。

オプションの第二引数 `precise` は、点が範囲にどのように入るかを検索する際に Julia Base の `TwicePrecision` を使用するかどうかを決定します。これは、点がビンのエッジにほぼ正確にある場合に便利ですが、正確には4倍遅くなるため、デフォルトでは `false` です。

分割の外にある点は確率に寄与しません。ビンは常に左閉右開です: `[a, b)`。**これは、各範囲の最後の値が最後の右閉じ値を決定することを意味します。** この値はヒストグラムには*含まれません*! 例えば、範囲 `r = range(0, 1; length = 11)` が与えられ、`r[end] = 1` の場合、値 `1` は分割の外にあり、最後のビン（ここでは `[0.9, 1)`) に対応する確率の増加には寄与しません!

**同等に、ヒストグラムのサイズは `histsize = map(r -> length(r)-1, ranges)` です!**

`FixedRectangularBinning` は、入力データの知識なしに明確に定義された結果空間をもたらします。詳細は [`ValueBinning`](@ref) を参照してください。
