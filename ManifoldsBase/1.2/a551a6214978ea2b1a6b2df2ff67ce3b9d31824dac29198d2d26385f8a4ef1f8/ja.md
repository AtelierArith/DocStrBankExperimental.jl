```
is_point(M::AbstractManifold, p; error::Symbol = :none, kwargs...)
is_point(M::AbstractManifold, p, throw_error::Bool; kwargs...)
```

`p`が[`AbstractManifold`](@ref) `M`上の有効な点であるかどうかを返します。デフォルトでは、関数は[`check_point`](@ref)を呼び出し、`ErrorException`または`nothing`を返します。

潜在的なエラーを報告する方法は、`error=`キーワードを使用して設定できます。

  * `:error`          - `p`が点でない場合にエラーをスローします
  * `:info`           - エラーメッセージを`@info`として表示します
  * `:warn`           - エラーメッセージを`@warning`として表示します
  * `:none` (デフォルト) – 関数は単に`true`/`false`を返します

他のすべてのシンボルは`error=:none`と同等です。

2番目のシグネチャはショートハンドであり、ブール値は`error=:error`（`true`）と`error=:none`（デフォルト、`false`）に使用されます。この場合、`error=`キーワードは無視されます。
