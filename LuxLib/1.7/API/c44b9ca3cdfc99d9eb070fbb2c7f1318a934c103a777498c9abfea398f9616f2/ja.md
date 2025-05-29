```
bias_activation!!(σ, x, bias)
```

[`bias_activation`](@ref) と同様ですが、可能であれば `x` をインプレースで更新することがあります。ユーザーは `x` が変更されることに依存すべきではなく、`y = bias_activation!!(σ, x, bias)` のように使用することをお勧めします。`x` がインプレースで更新される場合、`y` は `x` をエイリアスします。

他に [`bias_activation`](@ref)、[`fast_activation!!`](@ref) も参照してください。
