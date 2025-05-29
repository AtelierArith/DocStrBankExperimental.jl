```
normalize_position(pos, model::ABM{<:Union{AbstractGridSpace,ContinuousSpace}})
```

与えられた `model` の空間の範囲に対して正規化された位置 `pos` を返します。周期的な空間の場合、これは各次元に沿って位置をラップしますが、非周期的な空間の場合は位置を空間の範囲に制限します。
