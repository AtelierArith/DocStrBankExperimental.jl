受信したとおりにレスポンスボディを提供するように呼び出されます。

注意: S3クライアントで `enable_read_backpressure` を true に設定した場合、フロー制御ウィンドウを維持する必要があります。フロー制御ウィンドウは、このコールバックを介してボディデータを受信するにつれて縮小します。フロー制御ウィンドウが 0 に達すると、データのダウンロードが停止します。ウィンドウを増加させてデータの流れを維持するには、[`aws_s3_meta_request_increment_read_window`](@ref)() を使用してください。高いダウンロードスループットを維持するために、より大きなウィンドウを維持してください。パーツは、ウィンドウが複数のパーツを保持できるほど大きくない限り、並行してダウンロードできません。メモリにバッファリングされるデータの量を制限するには、より小さなウィンドウを維持してください。

`manual_window_management` が false の場合、フロー制御ウィンドウを維持する必要はありません。バックプレッシャーは適用されず、データは可能な限り速く到着します。

リクエストの処理を続行するには AWS*OP*SUCCESS を返します。

リクエストをキャンセルするには aws*raise*error(E) を返します。発生させたエラーは、`[`aws*s3*meta*request*result`](@ref).error_code` に反映されます。どのエラーを発生させるべきかわからない場合は、AWS*ERROR*S3_CANCELED を使用してください。
