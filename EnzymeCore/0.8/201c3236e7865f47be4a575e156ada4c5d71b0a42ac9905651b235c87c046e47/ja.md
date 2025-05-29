```
Active(x)
```

関数引数 `x` を [`autodiff`](@ref Enzyme.autodiff) のアクティブとしてマークします。Enzyme は `Active` 引数に関して自動微分を行います。

!!! note
    Enzyme の勾配は整数値に関してはゼロです。[`Active`](@ref) は通常の整数を浮動小数点値に自動的に変換しますが、タプルや構造体内の整数値に対しては変換できません。

