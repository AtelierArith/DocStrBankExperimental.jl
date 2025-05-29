このモジュールは、剰余算を紹介します。

整数 `x` mod. `n` は、関数 `Mod(x,n)` によって構築されます。もし `n` が `Int` の場合、結果は `Mod{UInt64}` 型になります。もし `n` が `BigInt` の場合、結果は `Mod{BigInt}` 型になります。`n` は型にエンコードされていないため、要素 `0` と `1` mod. `n` は型から構築することができず、これがいくつかのJuliaの機能に問題を引き起こします（例えば、行列に対する `inv` は機能しません）。素数剰余 `p` に対して、`FiniteFields` の型 `FFE{p}` にはそのような制限はありません。

例:

```julia-repl
julia> a=Mod(5,19)
Mod{UInt64}: 5₁₉

julia> a^2
Mod{UInt64}: 6₁₉

julia> inv(a)
Mod{UInt64}: 4₁₉

julia> a*inv(a)
Mod{UInt64}: 1₁₉

julia> a+2
Mod{UInt64}: 7₁₉

julia> a*2
Mod{UInt64}: -9₁₉

julia> a+1//2
Mod{UInt64}: -4₁₉

julia> Integer(a) # a から整数を取得
5

julia> order(a) # a の乗法的順序
9
```
