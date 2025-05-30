Websocketハンドシェイクリクエストの変換が完了したときに呼び出す関数。この関数は必ず呼び出さなければならず、さもなければアプリケーションはソフトロックします。

`request`と`complete_ctx`は、[`aws_mqtt_transform_websocket_handshake_fn`](@ref)に提供された同じポインタでなければなりません。`error_code`は、変換が成功した場合はAWS*ERROR*SUCCESSであるべきで、そうでない場合は別のAWS*ERROR*X値を渡してください。
