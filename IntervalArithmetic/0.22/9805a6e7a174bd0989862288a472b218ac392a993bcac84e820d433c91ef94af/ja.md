```
==(::BareInterval, ::Number)
==(::Number, ::BareInterval)
==(::Interval, ::Number)
==(::Number, ::Interval)
```

与えられた数のシングルトンであるかどうかをテストします。言い換えれば、結果はその区間がその数のみを含む場合にのみ真となります。

!!! note
    区間間の比較は故意に許可されていません。実際、非シングルトン区間間の等価性は特異な性質を持ち、特に $x = y$ は $x - y = 0$ を意味しません。代わりに [`isequal_interval`](@ref) を参照してください。

