```
ta_mergewith(f, l_array::TimeArray, r_array::TimeArray; kw...) -> TimeArray
```

左側と右側のTimeArrayの要素にバイナリ関数`f`を適用することで新しいTimeArrayオブジェクトを作成します。TimeArraysは対応する要素を確立するために以下のルールを使用します：

  * 最初の配列の要素は、2番目の配列の最も近い小さいまたは等しい要素にマッチします。
  * 2番目の配列にそのような要素がない場合、結果の要素は`NaN`になります。

## キーワード引数

  * `l_merge::Bool = true`: 結果のTimeArrayに`left`のタイムスタンプを使用します。
  * `r_merge::Bool = true`: 結果のTimeArrayに`right`のタイムスタンプを使用します。
  * `padding::Bool = true`: `NaN`値で最初のタイムスタンプを保持します。

## 例

```jldoctest
julia> using Dates

julia> t_left = TimeArray([
           TimeTick(DateTime("2024-01-02"), 0.2),
           TimeTick(DateTime("2024-01-05"), 0.5),
       ]);

julia> t_right = TimeArray([
           TimeTick(DateTime("2024-01-01"), 1.0),
           TimeTick(DateTime("2024-01-05"), 5.0),
           TimeTick(DateTime("2024-01-07"), 7.0),
       ]);

julia> ta_mergewith(+, t_left, t_right)
4-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-02T00:00:00, 1.2)
 TimeTick(2024-01-05T00:00:00, 5.5)
 TimeTick(2024-01-07T00:00:00, 7.5)

julia> ta_mergewith(-, t_left, t_right; l_merge = false)
3-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-05T00:00:00, -4.5)
 TimeTick(2024-01-07T00:00:00, -6.5)

julia> ta_mergewith(*, t_left, t_right, r_merge = false, padding = false)
2-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-02T00:00:00, 0.2)
 TimeTick(2024-01-05T00:00:00, 2.5)
```
