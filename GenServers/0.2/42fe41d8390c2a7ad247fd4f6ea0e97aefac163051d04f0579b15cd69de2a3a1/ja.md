```
GenServers
```

汎用サーバー `Actors` プロトコルを実装します。

サーバーのユーザーAPIと、特定のリクエストが発行された場合にサーバーによって呼び出されるコールバック関数を持つ実装モジュールを書くことができます。

`:genserver` アクターが同時実行性と分散部分を管理するため、純粋に逐次的なコードを書くことができます。これにより、サーバーの開発が大幅に簡素化されます。

現在の安定した登録バージョンは、次のコマンドでインストールできます。

```julia
pkg> add GenServers
```

開発バージョンは、次のコマンドでインストールできます。

```julia
pkg> add "https://github.com/JuliaActors/GenServers.jl"
```
