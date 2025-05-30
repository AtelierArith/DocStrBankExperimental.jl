`Actors`は古典的なアクターモデルを実装しており、`ActorInterfaces.Classic`で定義されたプリミティブに基づいています。提供する機能は以下の通りです：

  * アクターを作成し、メッセージを送信し、動作を変更するための基本的なプリミティブ：[`spawn`](@ref)、[`send`](@ref)、[`become`](@ref)と`Addr`および[`self`](@ref)、
  * アクターが受信したメッセージに対して実行される[`onmessage`](@ref)、
  * 事前定義されたメッセージを持つメッセージプロトコル、
  * プロトコルに基づいたAPIで、プリミティブ[`receive`](@ref)と[`request`](@ref)およびさらにAPI関数[`become!`](@ref)、[`call`](@ref)、[`cast`](@ref)、[`exec`](@ref)、[`exit!`](@ref)、[`init!`](@ref)、[`query`](@ref)、[`term!`](@ref)、[`update!`](@ref)、
  * アクターによるエラーハンドリング

      * 接続：[`connect`](@ref)、[`disconnect`](@ref)、[`trapExit`](@ref)、
      * モニター：[`monitor`](@ref)、[`demonitor`](@ref)、
      * スーパーバイザー：[`supervisor`](@ref)、[`supervise`](@ref)、[`unsupervise`](@ref)、[`start_actor`](@ref)、[`start_task`](@ref)、[`count_children`](@ref)、[`which_children`](@ref)、[`terminate_child`](@ref)、
  * アクター登録：[`register`](@ref)、[`unregister`](@ref)、[`whereis`](@ref)、[`registered`](@ref)

その他多数。

現在の安定した登録バージョンは以下のコマンドでインストールできます。

```julia
pkg> add Actors
```

開発バージョンは以下のコマンドでインストールできます：

```julia
pkg> add "https://github.com/JuliaActors/Actors.jl"
```
