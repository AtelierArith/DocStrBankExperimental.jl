publish(client::Client, topic::String, payload...; dup::Bool=false, qos::QOS=QOS_0, retain::Bool=false)

完全に確認されるまで待機します。指定されたパラメータでメッセージを公開します。成功した場合は `nothign` を返し、失敗した場合は例外をスローします。
