```
is_vector(M::AbstractManifold, p, X, check_base_point::Bool=true; error::Symbol=:none, kwargs...)
is_vector(M::AbstractManifold, p, X, check_base_point::Bool=true, throw_error::Boolean; kwargs...)
```

`X`が[`AbstractManifold`](@ref) `M`の点`p`で有効な接ベクトルであるかどうかを返します。`true`または`false`のいずれかを返します。

`check_base_point`がtrueに設定されている場合、この関数は最初に`p`に対して[`is_point`](@ref)を呼び出します。その後、関数は[`check_vector`](@ref)を呼び出し、返された値が`nothing`またはエラーであるかどうかをチェックします。

潜在的なエラーを報告する方法は、`error=`キーワードを使用して設定できます。

  * `:error`          - `X`が接ベクトルでない場合や`p`が点でない場合にエラーをスローします。

^ `:info`           - エラーメッセージを`@info`として表示します。

  * `:warn`           - エラーメッセージを`@warn`として表示します。
  * `:none`           - (デフォルト) 関数は単に`true`/`false`を返します。

他のすべてのシンボルは`error=:none`と同等です。

2番目のシグネチャはショートハンドであり、`throw_error`は`error=:error`（`true`）および`error=:none`（デフォルト、`false`）に使用されます。この場合、`error=`キーワードは無視されます。
