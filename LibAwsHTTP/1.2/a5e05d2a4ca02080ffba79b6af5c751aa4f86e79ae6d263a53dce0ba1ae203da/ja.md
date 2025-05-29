ヘッダーが受信されるたびに繰り返し呼び出されます。この時点で、クライアントには[`aws_http_stream_get_incoming_response_status`](@ref)()を呼び出すことができます。また、サーバーには[`aws_http_stream_get_incoming_request_method`](@ref)()および[`aws_http_stream_get_incoming_request_uri`](@ref)()を呼び出すことができます。これは常にHTTP接続のイベントループスレッドで呼び出されます。

ストリームの処理を続行するにはAWS*OP*SUCCESSを返します。失敗を示し、ストリームをキャンセルするにはaws*raise*error(E)を返します。あなたが発生させたエラーは、on*completeコールバックに渡されるerror*codeに反映されます。
