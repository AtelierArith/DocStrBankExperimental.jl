```
observed(indp, sym, [states])
```

与えられた `sym` の `indp` における観測関数を返します。返される関数は `(u, p) -> [values...]` というシグネチャを持ち、ここで `u` と `p` はそれぞれ現在の状態とパラメータオブジェクトです。もし `istimedependent(indp) == true` の場合、関数は現在の時間 `t` を第三のパラメータとして受け取る必要があります。もし `constant_structure(indp) == false` の場合、`observed` は第三のパラメータを受け入れ、これは状態の順序を示すシンボルのベクトルまたは状態の順序を特定する時間インデックスのいずれかです。この関数は、[`is_observed`](@ref) が常に `false` を返す場合には定義する必要はありません。したがって、この関数を使用する前に必ず `is_observed` を確認することが必須です。

もし `!is_markovian(indp)` の場合、返される関数は `(u, h, p, t) -> [values...]` というシグネチャを持ち、ここで `h` は過去の状態の値を取得するために呼び出すことができる履歴関数です。`h` の正確なシグネチャと意味は、返される関数内でどのように使用されるかによって異なります。`h` は、[`get_history_function`](@ref) を使用して値プロバイダーから取得されます。

参照: [`is_time_dependent`](@ref), [`is_markovian`](@ref), [`constant_structure`](@ref).
