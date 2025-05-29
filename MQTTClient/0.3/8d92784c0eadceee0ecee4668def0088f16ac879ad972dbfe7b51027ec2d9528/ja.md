publish_async(client::Client, message::Message)

メッセージを公開します。成功時には `nothing` を含む `Future` オブジェクトを返し、失敗時には例外を返します。
