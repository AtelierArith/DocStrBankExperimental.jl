S3クライアントのためのファクトリ関数で、S3 Express資格情報プロバイダーを作成します。S3クライアントはS3 Express資格情報プロバイダーの唯一の所有者となります。

S3クライアントの破棄中に、S3クライアントはプロバイダーの破棄を開始し、S3クライアントが破棄を完了する前に`on_provider_shutdown_callback`が呼び出されるのを待ちます。

ファクトリを適切に実装するための注意点：

  * `on_provider_shutdown_callback`は、プロバイダーのシャットダウンが完了した後に呼び出されることを確認してください。そうしないと、リークが発生します。
  * プロバイダーはクライアントへの参照を取得してはいけません。そうしないと、循環参照がデッドロックを引き起こします。
  * 提供された`client`は、ファクトリ関数呼び出しやデストラクタ内で使用できません。

# 引数

  * `allocator`: プロバイダーを作成するためのメモリアロケーター。
  * `client`: S3クライアントはプロバイダーを使用し、所有します。
  * `on_provider_shutdown_callback`: プロバイダーのシャットダウンが完了したときに呼び出されるコールバック。
  * `shutdown_user_data`: シャットダウンコールバックを呼び出すためのユーザーデータ
  * `user_data`: ファクトリに関連するユーザーデータ

# 戻り値

[`aws_s3express_credentials_provider`](@ref)。
