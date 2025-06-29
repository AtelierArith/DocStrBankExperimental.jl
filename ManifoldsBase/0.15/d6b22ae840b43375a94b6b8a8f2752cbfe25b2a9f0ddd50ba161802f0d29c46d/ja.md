```
isapprox(M::AbstractManifold, p, X, Y; error:Symbol=:none; kwargs...)
```

点 `p` で接するベクトル `X` と `Y` が、[`AbstractManifold`](@ref) `M` においておおよそ等しいかどうかを確認します。

オプションの位置引数は、結果が偽の場合に具体的な多様体がそのような情報を提供する場合に、より多くの情報を得るために使用できます。現在、以下がサポートされています。

  * `:error` - `isapprox` が偽と評価された場合にエラーをスローし、より詳細なエラーを提供します。これは基本的に `isapprox` を `@assert` に変えます。
  * `:info` – `@info` で情報を印刷します。
  * `:warn` – `@warn` で情報を印刷します。
  * `:none` (デフォルト) – 関数は単に `true`/`false` を返します。

デフォルトでは、これらの情報は [`check_approx`](@ref) を呼び出すことによって収集されます。

キーワード引数は、許容誤差を指定するために使用できます。
