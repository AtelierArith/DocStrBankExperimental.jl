`random_choice(weights)` は、`1` から `n` までの値をランダムに選択します。ここで、`n` は `weights` の要素数です。`k` が選ばれる確率は `weights[k]` に比例します。`weights` は非負であり、すべてがゼロではない必要があります。

`random_choice(dict)` は、重みが `dict[k]` に比例するように `dict` からランダムなキー `k` を選択します。したがって、`dict` は `Dict{S, T<:Real}` 型でなければなりません。
