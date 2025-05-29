高ブーストバターワースフィルタを構築します。

```
Usage: f = highboostfilter(sze, cutoff, n, boost)

Arguments:
         sze - フィルタのサイズを指定する2要素のタプル
               (行, 列)。
      cutoff - フィルタのカットオフ周波数 0 - 0.5
           n - フィルタの次数。nが大きいほど遷移が鋭くなります。
               (nは1以上の整数でなければなりません)。
       boost - 高周波数値が低周波数値に対してどれだけブーストされるかの比率。
               boostが1未満の場合は「ローブースト」フィルタが生成されます。
Returns:
           f - サイズがszeの周波数領域フィルタ。周波数
               原点はコーナーにあります。
```

参照: [`lowpassfilter`](@ref), [`highpassfilter`](@ref), [`bandpassfilter`](@ref)
